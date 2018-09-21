# 公网访问方法
*提醒：公网访问消息队列 JCQ的方式仅可用于测试，生产环境请勿使用。*  

## 前提
要在公网使用jcq sdk收发消息，需满足如下前提条件：拥有一台 Linux 系统的京东云主机，并已绑定公网 IP。

## 1. 代理设置

 本地安装一个proxy client, 如Proxifier、ProxyCap等，并配置代理规则，下面以Proxifier为例说明

### 1.1 配置代理服务器
 配置文件->代理服务器->添加  
 地址：127.0.0.1  
 端口：填写一个本地未使用端口，如19999  
 协议： 选择SOCKS 版本 5  
 验证：不启用  

![公网访问-01](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/公网访问-01.png)
 

### 1.2 配置代理规则

配置文件->代理规则->添加  
名称：随意填（如jcq proxy rule）   
应用程序：任意  
目标主机：*.jvessel-open-hb.jdcloud.com  
目标端口：任意  
动作：选择刚刚创建的代理服务器  


![公网访问-02](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/公网访问-02.png)

注意Default规则的动作选择Direct, 这样jcq以外网络流量不走代理。  


![公网访问-03](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/公网访问-03.png)



## 2. SSH端口转发配置

本地安装SecureCRT、Xshell等ssh client， 下面以SecureCRT为例说明如何配置端口转发规则  

### 2.1 建立连接
协议：SSH2  
 主机名：填写用户自己的云主机公网ip  
端口：22  
 防火墙：无  
用户名：root  

![公网访问-04](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/公网访问-04.png)

### 2.2 配置端口转发规则

选项->会话选项->连接->端口转发  


![公网访问-05](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/公网访问-05.png)


![公网访问-06](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/公网访问-06.png)

添加端口转发规则  

名称：随意填（比如jcq forward rule）   

手工选择允许连接的本地ip地址：勾选  

IP地址： 127.0.0.1  

端口：填写步骤1.1中代理中配置的本地端口， 本例是19999  

远程：勾选‘使用SOCKS 4或5动态转发’  


![公网访问-07](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/公网访问-07.png)



## 3. 使用sdk收发消息

满足下面前提条件，即可在本地使用sdk收发消息  

前提条件：
- 确保步骤1中的proxy client处于运行状态  
- 确保步骤2中的配置的连接处于连接状态  
