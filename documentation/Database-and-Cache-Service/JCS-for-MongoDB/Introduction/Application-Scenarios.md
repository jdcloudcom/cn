# 应用场景

以下说明云数据库 MongoDB 的适用场景。

## 同城容灾
云数据库 MongoDB 支持多可用区部署模式，您可以将实例的主从节点与隐藏节点分别部署在不同的可用区，以提供同城容灾能力。当因不可抗力导致某一可用区不能提供服务时，MongoDB 服务可快速切换到另一可用区，确保服务的可用性。

![同城容灾场景](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mogno-001.png)


## 分服应用
依托云数据库 MongoDB 完善的备份机制和根据时间点创建实例的能力，您可以快速基于某一实例的数据创建新的 MongoDB 实例，以满足游戏等分区服务类应用的快速滚服和合服的需求。

![分服应用场景](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-002.png)

## 相关参考

- [产品优势](../Introduction/Benefits.md)
- [产品功能](../Introduction/Features.md)
- [价格总览](../Pricing/Price-Overview.md)
- [计费规则](../Pricing/Billing-Rules.md)
- [创建实例](../Getting-Started/Create-Instance.md)
