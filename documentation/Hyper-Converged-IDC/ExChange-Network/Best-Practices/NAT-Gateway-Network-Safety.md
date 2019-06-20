# NAT网关网络安全方案

## 概述
NAT网关是通过定制安全策略允许到达与其相关联的云物理服务器（简称CPS）的入站流量，以及允许离开云物理服务器的出站流量。默认情况下，NAT网关（拒绝）所有流量。NAT为云物理服务器CPS提供有状态的防火墙，能够指定并记住为发送或接收信息包所建立的连接的状态，是一套用来设置、维护和检查云物理服务器外网通信的安全机制。

## 应用场景介绍
内网的CPS访问公网，仅需要一台云物理服务器有一个公网和一个内网IP，其他的云物理服务器都只需一个内网IP，通过这台有公网IP的服务器做NAT网关，就可以实现所有的云物理服务器访问公网，用户还可以按照业务需要，仅仅允许特定的云物理服务器访问公网。

同理，公网访问内网的CPS，通过这台有公网IP的服务器做NAT网关，映射相应的IP和端口号，就可以实现公网访问CPS的业务应用系统或远程管理CPS.

通过NAT网关，简化了网络架构，降低了公网IP的数量，增强了内网CPS和业务应用系统的网络安全。

## 网络架构示意图

![网络架构示意图](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS024.png)

## 配置方案
配置命令的IP信息都是模拟的，请以购买的云物理服务器的IP信息替换。


**注意**：请谨慎关闭SSH登录22端口，关闭22端口会造成您不可从外部访问NAT网关和云物理服务器！

### 内网CPS访问公网的配置方案

#### 修改云物理服务器

1、通过NAT网关，SSH登录内部Server ssh root@172.16.0.4 （密码是购买时手动设置的密码）

2、默认IP信息，【图1.0】和路由信息【图1.1】

![IP信息图1.0](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS025.png)

<p align="center">IP信息【图1.0】</p>

![路由信息图1.1](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS026.png)

<p align="center">路由信息【图1.1】</p>

3、修改云物理服务器为NAT网关的内网IP（如172.16.0.3）：

vim /etc/sysconfig/network-scripts/ifcfg-eth0,添加一条`GATEWAY=172.16.0.3`，保存退出wq，重启服务生效service network restart.

![修改默认网关图2.0](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS027.png)

<p align="center">修改默认网关【图2.0】</p>

![查看默认路由的网关图2.1](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS028.png)

<p align="center">查看默认路由的网关【图2.1】</p>

#### 配置NAT网关系统策略

1、开启系统的路由转发功能：

编辑vim vi /etc/sysctl.conf 文件，修改`net.ipv4.ip_forward = 1`；sysctl –p 不用重启系统，配置生效。

![开启路由转发功能](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS029.png)

2、添加 FORWARD 转发规则

默认的 iptables 的策略是不允许流量的转发，所以我们需要先删除默认的不允许转发的规则；`iptables -D FORWARD 1` ，其中 `1` 代表 FORWARD 规则中的第一条规则。因为默认的只有一条 FORWARD 规则，所以只需要删除第一条即可。

![默认forward转发规则图2.0](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS030.png)

<p align="center">默认forward转发规则【图2.0】</p>


`iptables -A FORWARD -s 172.16.0.0/16 -i eth0 -j ACCEPT`


允许转发来自内网网段（172.16.0.0/16）来自于内网网卡 eth0 的流量转发。


`iptables -A FORWARD -m state --state RELATED,ESTABLISHED  -j ACCEPT`


允许转发已经建立好链接的流量，不允许来自外网新的请求流量进来。

![forward转发规则图2.1](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS031.png)

<p align="center">forward转发规则【图2.1】</p>

3、配置SNAT（内部CPS通过NAT网关访问公网）：

```
iptables -t nat -A POSTROUTING -s 172.16.0.0/16 -o eth1 -j SNAT --to-source 103.37.46.14
```

![SNAT策略规则图3.0](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS032.png)

<p align="center">SNAT策略规则【3.0】</p>

4、保存配置

service iptables save

### 公网访问CPS的配置方案

1、添加filter安全规则：

允许相应的业务被访问，如SSH 22、NTP 123、http80等TCP、UDP、ICMP服务。

```
Iptables -A INPUT -i eth1 -p tcp -m state --state NEW -m tcp --dport 22 -j ACCEPT
iptables -A INPUT -i eth1 –p udp -m state --state NEW -m tcp --dport 123 -j ACCEPT
iptables -A INPUT -i eth1 -p tcp -m state --state NEW -m tcp --dport 80 -j ACCEPT
```

2、	配置DNAT（公网通过NAT网关访问云物理服务器）
将TCP 8888端口号，映射到CPS的SSH 22端口。

```
Iptables –t nat -A PREROUTING -p tcp -m tcp --dport 8888 -j DNAT --to-destination 172.16.0.4:22
```

![DNAT策略规则图2.0](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS033.png)

<p align="center"> DNAT策略规则【2.0】</p>

                         
3、保存配置

service iptables save
