授权策略（Policy）是定义一条或多条权限的 JSON 文档。本文介绍了 IAM Policy 的基本元素、语法结构和示例。

# Policy 的基本元素
IAM Policy 包含以下基本元素：content（策略内容）、permission（允许的操作类型）、resource（允许操作的资源）、ids（指定资源的 IDs）、type（指定资源的类型）和 version（策略版本）。

 - content

Policy 的内容包含一组或多组授权详情。每一组授权详情都指定了被授权的资源（resource）和操作（permission）。

 - permission

支持 3 种类型的资源操作，即读（R，指 Read）、改（M，指 Modify）、删除（D，指 Delete）。例如，查看云主机详情是读操作，备份或重启云主机均属于改操作，删除镜像是删除操作。
当需要授权多种操作类型时，可以用竖线 "|" 将操作类型隔开。如，仅授权只读操作时，permission 为 "R"；授权管理员权限时，permission 为 "R|M|D"。
注：如果授权子账号改权限（M）和删除权限（D），则子账号默认也具有读权限（R）。

 - resource

被授权的资源由资源类型（type）和资源 ID （ids） 指定。

 - type

指定被授权的资源类型。附表-1 列举了目前 IAM 支持的所有资源的 type 值。

|资源类型|type 值|
|---|:--:|
云主机|server
镜像|image
云硬盘|volume
公网 IP|floatingIP
负载均衡|loadbalance
云数据库 (MySql)|database
云缓存|cache
VPC|vpc
子网|vpc
安全组|vpc
路由表|vpc
网络 ACL|vpc
DDoS 基础防护|baseanti
应用安全网关|sgw
主机安全|hips
态势感知|ids

 - ids

指定被授权的一个或多个资源 IDs。ids 支持通配符 *，用于授权对象是某一类资源，而不是指定资源 ID 的场景。

 - version

Policy 的版本，目前仅允许值为 2。

# Policy 的语法结构
Policy 的语法结构如下图所示。

![语法结构](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Strategy%20Management/policy%E8%AF%AD%E6%B3%95%E7%BB%93%E6%9E%84.png)

Policy 的语法应符合 JSON 格式。如果您创建的授权策略不符合 JSON 语法，将无法保存成功。很多在线 JSON 格式检查工具都可以检查策略的格式错误。

# Policy 的语法描述：

	<policy> =
		{
		          <content>,
		          <version>
		}
		
		其中 Content 的描述可以包含一组或多组 Permission 和 Resource 对：
		
		<content> = 
		"content":[
		          {
		                    <permission>,
		                    <resource>
		          },
		          {
		                    <permission>,
		                    <resource>
		          }
		]
		
		Permission 为（以管理员权限为例）：
		
		<permission> = 
		"permission" : "R|M|D"
		
		Resource 中需要指定资源的类型和 IDs：
		
		<resource> =
		"resource":[
		          {
		                    <ids>,
		                    <type>
		          }
		]
		
		IDs 指定一个或多个资源（以指定资源 ID 为例）：
		
		<ids> = 
		"ids":[
		          "resource-id1",
		          "resource-id2"
		]
		
		Type 指定该资源的类型（"resource-type" 请参考 附表-1）：
		
		<type>  = 
		"type":"resource-type"
		
		Policy 中的 Version 元素固定值为 2：
		
		<version> = 
		"version":"2"


# Policy 示例
下述 Policy 策略描述了如下授权场景：

一个指定的 VPC 的读、改权限

三个 MySql 云数据库实例的管理员权限

两台云主机实例的只读权限

全部镜像资源的管理员权限

		{
		          "content":[{
		                    "permission":"M",
		                    "resource":[{
		                              "ids":["vpc-3dodmrqvz0"],
		                              "type":"vpc"
		                    }]
		          },
		          {
		                    "permission":"M|D",
		                    "resource":[{
		                              "ids":["mysql-hgrgehgage",
		                                       "mysql-grigg0k7w8",
		                                       "mysql-x53es4bxer"],
		                              "type":"database"
		                    }]
		          }, 
		          {
		                    "permission":"R",
		                    "resource":[{
		                              "ids":["i-p26ionqsok",
		                                       "i-37dotxi75d"],
		                              "type":"server"
		                    }]
		          },
		          {
		                    "permission":"M|D",
		                    "resource":[{
		                              "ids":["*"],
		                              "type":"image"
		                    }]
		          }],
		          "version":"2"
		}
