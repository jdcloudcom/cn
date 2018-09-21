# 查看监控信息

消息队列 JCQ控制台提供了丰富的性能监控数据，您可以随时查看订阅关系的运行状态。

## 操作步骤
1. 登录 [消息队列 JCQ 控制台](https://jcq-console.jdcloud.com/topics)。
1. 在“Topic管理”页面，选择目标topic，点击 **topic名称**，进入”topic详情“页面。
1. 在”topic详情“页面，点击 **监控**，查看监控信息。



   - 您可以快速选择查看1小时至14天的数据，也可以输入日期范围查看，时间范围最长可选择1个月。
   - 支持查看Topic和topic下某个Consumer Group的监控信息
   
   
![监控3](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/监控-03.png)
![监控4](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/监控-04.png)

## 监控项说明
类型 | KPI | 说明
--- | --- | ---
Topic | 生产的TPS（条/秒）| 每秒钟生产的消息数量|
Topic| 已发布消息的数量(个)|生产者发送消息到主题的消息数量|
Topic|已发布消息的请求量(次)|生产者发送消息到主题的API请求数量|
Topic| 已发布消息的大小(byte)|生产者发送消息到主题的消息大小|
Consumer Group| 消费的TPS（条/秒）|每秒钟消费的消息数|
Consumer Group| 堆积消息数量（个）|订阅关系中堆积的消息数量
Consumer Group| 接收消息请求量(次)|订阅关系中消费者拉取的请求数量
Consumer Group|接收的消息数量（个）|订阅关系中消费者拉取的消息总数量|
Consumer Group|成功接收消息数量（个）|订阅关系中消费者拉取成功的消息数量|
Consumer Group|接收消息的大小（byte）|订阅关系中消费者消费的消息大小|
