# 公网连接 MongoDB 实例

## 背景信息
云数据库 MongoDB 目前不提供公网连接，如果您需要本地连接云数据库 MongoDB 实例，可以通过云主机代理转发的方式实现。

## 注意事项

- 通过公网连接 MongoDB 实例的方式仅可用于测试环境，生产环境请勿使用。
- 通过云主机代理的方式连接， MongoDB 实例不支持Connection String URI的连接方式，无法保证实例高可用。

	

## 方式1：以SecureCRT为例，通过监听本地端口实现代理转发。



### 前提条件

一台绑定了公网IP的Linux系统的云主机，并与云数据库MongoDB在同一VPC，且未通过ACL、安全组等限制云主机的连接。

### 操作步骤

1. 本地电脑安装SecureCRT，以SSH2协议远程连接到有公网IP的云主机。
   
   - 选择 **Connection**，填写名称、选择协议为SSH2。
  
      ![](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-031.png)

   - 选择 **SSH2**，填写作为代理的主机信息。
   
      Hostname：填写云主机的公网IP。

      Port：可默认22。
      
      Username：填写云主机的登录用户名，默认为“root”。
      
      ![](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-032.png)

1. 设置端口转发规则。
   - 选择 **Port Forwarding**，点击 **Add**。

      ![](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-033.png)

   - 填写端口转发相关信息。
   
      Name：填写名称

      Port：填写本地的监听端口，大于1024小于65535即可，如填写27019。
      
      填写云数据库MongoDB的域名(可在实例详情页查看)。
      
      填写云数据库MongoDB的端口，为27017。
      
      ![](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-034.png)

1. 保存设置，并连接云主机。
1. 本地连接 MongoDB 实例。

   连接地址：填localhost或127.0.0.1。
   
   端口：监听的本地端口，如上文的27019。
   
   账号、密码：MongoDB 实例设置的账号密码信息。

## 方式2：在云主机上设置转发规则，以下以socat为例说明。

### 前提条件

一台绑定了公网IP的Linux系统的云主机，并与云数据库MongoDB在同一VPC，且未通过ACL、安全组等限制云主机的连接。

### 操作步骤

1. 登录云主机。
1. 安装socat。
   > yum install -y socat

2. 添加代理规则。
   > socat TCP-LISTEN:27019,fork TCP:jmongo-hb1-prod-mongo-xxxx.jmiss.jcloud.com:27017

   - TCP-LISTEN:填写监听端口，如上文的27019。
   - TCP：您的云数据库MongoDB的连接地址和域名。

1. 本地连接本地连接云数据库MongoDB实例。
   - 连接地址：填云主机的公网IP。
   - 端口：监听端口，如上文的27019。
   - 账号、密码：云数据库MongoDB设置的账号密码信息。
   
### 相关参考

- [连接实例](../Getting-Started/Connect-Instance.md)
- [云主机无法连接 MongoDB 实例?](..//Troubleshooting/Connect-Failed.md)
