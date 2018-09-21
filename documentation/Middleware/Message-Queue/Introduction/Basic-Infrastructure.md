# 基础架构
消息队列 JCQ的集群结构，同步写入三副本备份，保证服务的高可靠性和高可用性，自主研发的的框架保证服务的高性能，来满足不同业务的需求。

## 业务架构
业务架构如下图：
![](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/basic-infrastructure.jpg)

| 概念 | 解释 |
| :- | :- |
| Broker Group | 消息队列 JCQ核心组件，负责消息存储、订阅管理、消费管理和数据统计等功能 |	
| Meta Manager Cluster | 消息队列 JCQ核心组件，负责消息路由、授权、控制事务等功能 |
| 控制服务 | 处理来自用户和后端的请求任务，主要有创建、删除、查询、配置修改、重置消费位点等任务 |
| 监控服务 | 收集消息队列 JCQ Topic和Consumer Group的信息，供用户和控制台展现 |
| 日志服务 | 收集消息队列 JCQ日志信息 |
| 计费服务 | 负责统计用户的请求量计算费用 |


## 相关参考

- [产品优势](../Introduction/Benefits.md)
- [产品功能](../Introduction/Features.md)
- [价格总览](../Pricing/Price-Overview.md)
- [计费规则](../Pricing/Billing-Rules.md)


