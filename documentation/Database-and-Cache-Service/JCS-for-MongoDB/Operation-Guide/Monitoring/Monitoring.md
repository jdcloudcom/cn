# 查看监控信息

MongoDB 控制台提供了丰富的性能监控数据，您可以随时查看实例的运行状态。

## 操作步骤
1. 登录 [MongoDB 控制台](https://mongodb-console.jdcloud.com/mongodb)。
1. 在“实例列表”页面，选择目标实例，点击 **实例名称**，进入”实例详情“页面。
1. 在”实例详情“页面，点击 **监控**，查看监控信息。

   ![](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-024.png)

   - 您可以快速选择查看1小时至14天的数据，也可以输入日期范围查看，时间范围最长可选择1个月。
   - 支持查看primary节点与secondary节点的监控信息。
	

## 监控项说明

监控项	| 说明
--- | ---
CPU使用率	| 实例的CPU利用率。
内存利用率	| 实例的内存利用率。
磁盘使用率	| 实例总使用空间与规格最大可使用空间的比值。
IOPS使用率	| 实例使用IOPS大小与最大可用IOPS的比值
connections	| 实例的连接数
opcounters	| 实例的操作QPS数，包括：<br />	- insert操作数<br />	- query操作数<br />	- delete操作数<br />- update操作数<br />	- getmore操作数<br />	- command操作数<br />
network	 | 实例的网络流量，包括：<br />	- 进口流量<br />	- 出口流量<br />	- 处理的请求数<br />
cursors	| 实例使用的cursor数，包括：<br />	- 当前cursor打开数量<br />	- cursor超时数量<br />
globalLock	| 实例当前等待全局锁的队列长度，包括：<br />	- 全局读锁的等待队列长度<br />	- 全局写锁的等待队列长度<br />	- 所有全局锁的等待队列长度<br />
wiredTiger	| 实例wiredTiger引擎cache层指标，包括：<br />	- 读入cache的数据量大小<br />	- 从cache写的磁盘大小<br />	- 配置最大可用的磁盘大小<br />



	
## 相关参考

- [设置报警规则](Alarm-Rules.md)
	




	
	


