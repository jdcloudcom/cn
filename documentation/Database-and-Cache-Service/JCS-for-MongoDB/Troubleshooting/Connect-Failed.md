# 云主机无法连接 MongoDB 实例

## 问题描述
使用云主机连接 MongoDB 数据库时报错，无法连接，提示：exception: connect failed，具体提示参考下图。

![](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-027.png)

## 问题分析

可能原因为云主机与MongoDB 实例的链路不通。

## 问题处理

1. 确认 MongoDB 实例的连接地址是否正确。

   在 MongoDB控制台找到该实例，在实例详情页查看 MongoDB 连接地址。请参考：[连接实例](../Getting-Started/Connect-Instance.md)

1. 确认用于连接的云主机是否与 MongoDB 实例是否在同一个VPC。

   在京东云控制台查看云主机与 MongoDB 实例是否处于同一个VPC内，如两者处于不同VPC，且未通过VPC对等连接打通，则内则网络不通，请更换用于连接 MongoDB 实例的云主机。

1. 确认 MongoDB 实例的白名单是否限制了云主机的IP？

   在 MongoDB 控制台找到该 MongoDB实例，查看其白名单设置。确认云主机的内网IP是否被白名单限制，如受限，请将其加入白名单。

1. 确认云主机的安全组规则是否做了限制。

   在云主机控制台，找到台该云主机，查看其安全组规则，如出站规则未开通27017端口，请添加规则：
   - 类型：自定义TCP
   - 目的端口：27017
   - 目的IP：0.0.0.0/0，因MongoDB 实例在自动容灾切换或扩容时IP可能会变化，请开通全部IP。
	![](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-028.png)
	
1. 确认云主机与MongoDB所在子网使用的网络 ACL 是否做了限制。

   在私有网络控制台，找到云主机和 MongoDB 所在的子网使用的网络ACL，确认其出站规则与入站规则是否开通27017端口，如未开通，请添加规则：
   - 类型：自定义TCP
   - 目的端口：27017
   - 目的IP：0.0.0.0/0，因MongoDB 实例在自动容灾切换或扩容时IP可能会变化，请开通全部IP。
   ![](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-029.png)

  ## 后续处理
  如通过以上步骤排查仍未解决问题，请 [提交工单](https://ticket.jdcloud.com/myorder/form?cateId=166&questionId=238) 或 致电客服 400-615-1212 。


