# 连接实例

出于安全考虑，云数据库 MongoDB 目前仅提供内网连接，暂不提供公网连接。

如果您需要本地直接连接云数据库 MongoDB 实例，可以通过云主机代理转发的方式实现，操作方式请参考 [公网连接 MongoDB 实例](../Best-Practices/Public-Network-Connect-to-MongoDB-Instance.md)。



## 前提条件
- MongoDB 实例状态为运行，且计费状态正常。
- MongoDB 实例与用于连接云主机处于同一个VPC内，且未通过ACL、安全组、白名单等限制两者连通。

## 操作步骤
1. 获取 MongoDB 实例的连接信息。
   1. 登录 [MongoDB 控制台](https://mongodb-console.jdcloud.com/mongodb)。
   1. 在“实例列表”页面，选择目标实例，点击 **实例名称** ，进入“实例详情”页面。
   1. 在“实例详情”页面，查看资源信息，获取 MongoDB 实例的连接信息。
   
		![查看连接](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-006.png)

		- 数据库名称，默认为admin 。
		- 用户名称，默认为root 。
		- 副本集名称。
		- 连接地址。
				
		   默认情况下，节点1为Primary， 节点2为Secondary，	如发生自动容灾切换等情况，Primary、Secondary节点可能发生变化。
                客户端请使用Connection String URI连接来保证高可用。

2. 连接 MongoDB 实例。
   - 使用Mongo shell 连接

		mongo shell是MongoDB自带的一种交互式JavaScript shell。您可以使用mongo shell查询和更新数据或执行管理操作。
		
		mongo shell是MongoDB发行版的一部分，您需要先安装MongoDB，然后再使用mongo shell 连接至您的MongoDB实例。
		
		MongoDB发行版下载地址请参见：[MongoDB Download Center](https://www.mongodb.com/download-center#community) 。
		
		请使用 mongo shell 3.2及以上版本的 client 连接 MongoDB 实例 ，否则可能无法鉴权成功。
		
		在云主机上使用 mongo 命令进行连接，命令样例如下：

		> mongo --host jmongo-xxx.jmiss.jcloud.com:27017 --authenticationDatabase admin -u root -p
		
		> mongo --host jmongo-xxx.jmiss.jcloud.com:27017 --authenticationDatabase admin -u root -p
		
		或者
		
		> mongo mongodb://root:****@jmongo-xxx.jmiss.jcloud.com:27017,jmongo-xxx.jmiss.jcloud.com:27017/admin?replicaSet=mgset-xxx
		
		>（****部分替换为root密码）
		
   - 使用Connection String URI连接实例
   
      MongoDB服务可以用传统的传参的方式进行连接，同时大部分的驱动程序也支持URI形式进行连接，MongoDB官方推荐使用URI的方式连接MongoDB服务以保证连接高可用。请使用MongoDB 3.2以上版本的driver。
		
      命令样式如下：

	   > mongodb://root:****@jmongo-xxx.jmiss.jcloud.com:27017,jmongo-xxx.jmiss.jcloud.com:27017/admin?replicaSet=mgset-xxx
	   
	   > （****部分替换为root密码）
		
		
## 相关参考

- [公网连接 MongoDB 实例](../Best-Practices/Public-Network-Connect-to-MongoDB-Instance.md)
- [问题处理：云主机无法连接 MongoDB 实例](../Troubleshooting/Connect-Failed.md)
- [问题处理：登录数据库提示无权限](../Troubleshooting/Authentication.md)
		
