# SSH无法远程登录排查

在实际操作过程中有时会出现无法远程登录的情况，这里简单介绍了SSH无法登录的可能原因及排查方法，帮助您用以自测。



在操作实例中，首先可在控制台检查是否开启了防火墙或配置了相关安全组，阻止用户远程登录，通过关闭防火墙或者打开远程登录的端口号便可正常使用。

除此之外，大部分实例可归结至以下三种现象问题：客户端问题、中间网络问题和SSH 服务配置问题。

**1、客户端问题**

客户端无法正常登录时，建议先通过使用不同的 SSH 客户端进行登录测试。若可正常登录，则判断是客户端配置问题，需要自行对客户端配置或软件运行情况做排查。新手需要注意的是，Linux客户端应该使用Putty或Xshell，mstsc是Windows操作系统远程登录命令，若您使用的是mstsc，建议先更换客户端噢。

**2、中间网络问题**

客户端无法正常通过 SSH 连接服务器时，可通过如下方法进行 telnet 端口测试，判断ping包通信是否正常：

telnet <服务器 ip="">
正常情况下，会返回服务端 SSH 软件版本号。

如果端口测试失败，客户端访问目标服务器出现 ping 丢包或 ping 不通时，可以通过 tracert 工具进行链路测试，判断链路是否联通。


**3.SSH 服务配置问题**

首先需要确定SSH是否提供了对外的服务，命令如下：

*[root@~]# netstat –ntlp | grep sshd*

*tcp     0     0 0.0.0.0:22             0.0.0.0:*        LISTEN    1132/sshd*

*tcp     0     0  : : :22                0.0.0.0:*        LISTEN    1132/sshd*



通过以上确定是否有SSH程序在运行，若尚未运行，先启动命令开启SSH服务（CentOS 6.X 默认的启动命令是service sshd start）；另外需要看一下ssh程度的监听端口是否有被修改，若被修改，则需要确定服务器的iptables与控制台的防火墙，是否做了相应的修改。0.0.0.0 表示全部地址都监听，若这里是127.0.0.1 那么代表只能本机上 ssh 连接的，需要修改/etc/ssh/sshd_config调整配置。

需要留意的是，系统卡死有可能是因资源耗尽导致，可从控制台查看CPU，检查是否是因内存过高导致无法连接，此时请关闭不必要的服务或重置服务器、升级配置。

**4.检查hosts.deny**
 
通过控制台远程登录方式登录云主机，排查/etc/hosts.deny；

 cat /etc/hosts.deny 是否存在denyIP地址，当IP地址被加入到该文件中后，该地址将无法登录（防护时间30分钟，30分钟后自动清除）；    vim /etc/hosts.deny 删除文件内IP地址即可；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/SSH%E6%97%A0%E6%B3%95%E8%BF%9C%E7%A8%8B%E7%99%BB%E5%BD%95%E6%8E%92%E6%9F%A501.png)

如果删除后再次被加入到hosts.deny中，您可以将本地出口IP地址加入到hosts.allow中，

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/SSH%E6%97%A0%E6%B3%95%E8%BF%9C%E7%A8%8B%E7%99%BB%E5%BD%95%E6%8E%92%E6%9F%A502.png)

以上，便是SSH无法远程登录的部分原因，如无法解决您的问题，请向我们提工单。
