# 产品概述
分布式数据库 TiDB 是京东云联合 PingCAP 基于国内开源 NewSQL 数据库 TiDB 打造的一款同时支持 OLTP 和 OLAP 两种场景的分布式云数据库产品，实现了自动的水平伸缩，强一致性的分布式事务，部署简单，在线异步表结构变更不影响业务，同时兼容 MySQL 协议，使迁移使用成本降到极低。

## 支持版本
目前北京地域支持TiDB 2.1.8 版本

## 分布式数据库 TiDB 主要特点 
1. 分布式数据库 TiDB 可随着数据增长而无缝地水平扩展节点数目，近似线性的提高计算能力和存储能力；
2. 一致性的分布式事务，支持标准的 ACID 事务，跨多个机器启动事务，不影响一致性；
3. 支持绝大多数 MySQL 语法，高度兼容MySQL，从 MySQL 无缝切换到 TiDB，几乎无需修改代码，迁移成本极低；
4. 使用多副本进行数据存储，主副本故障时自动切换，无需人工介入，自动保障业务的连续性，实现真正意义上的异地多活；

## 常用操作
- [创建实例](../Operation-Guide/Instance/Create-Instance.md)
- [连接实例](../Operation-Guide/Instance/Connect-Instance.md)
- [节点管理](../Operation-Guide/Node-Management.md)
- [重置密码](../Operation-Guide/Reset-Password.md)
- [监控](../Operation-Guide/Monitor.md)
  
## 计费
TiDB 目前处于公测阶段，暂时对通过申请的用户免费。
