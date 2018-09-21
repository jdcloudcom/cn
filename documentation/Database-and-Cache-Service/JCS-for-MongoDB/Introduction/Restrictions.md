# 限制说明

您可以快速创建并使用云数据库 MongoDB，但使用中有部分约束条件需要注意。

## 存储引擎
存储引擎默认为 WiredTiger，不支持修改。

## 副本集
系统自动搭建三节点的副本集，角色分别为 primary、secondary、hidden，其中 primary 节点、secondary 节点对用户可见，hidden 节点对用户不可见，用户不可自行搭建节点。
## oplog大小
oplog默认为存储空间的5%，不可修改。
## 连接数限制
连接数与您购买实例的规格相关，以下是各规格的最大连接数说明:

| 规格代码	| 规格	| 最大连接数 |
| :- | :- | :- |
|mongo.s1.small	|1核2G	|500|
|mongo.s1.medium	|2核4G	|1000|
|mongo.s1.large	|4核8G	|2000|
|mongo.s1.xlarge	|8核16G|	4000|
|mongo.s2.2xlarge	|8核32G|	8000|
|mongo.s2.4xlarge	|16核64G|	16000|

## 相关参考

- [产品概述](../Introduction/Product-Overview.md)
- [价格总览](../Pricing/Price-Overview.md)
- [创建实例](../Getting-Started/Create-Instance.md)
- [变更配置](../Operation-Guide/Instance-Management/Modify-Instance-Spec.md)
