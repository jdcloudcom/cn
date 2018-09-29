# 产品功能

## 轻松使用

### 快速创建
通过 MongoDB 控制台或简单的 API 调用，几分钟内即可创建 MongoDB 实例。

### 弹性扩容
支持扩容缩容，可根据业务情况按需升级或降级实例配置，提高资源利用率，降低使用成本。

## 服务可用性

### 三节点副本集

自动搭建三节点副本集，默认 Primary 和 Secondary 节点提供服务，当 Primay 节点出现故障时，系统自动选举新的 Primary 节点；当 Secondary 节点不可用时，由备用节点接管服务，多重保障机制确保服务可用性。

### 单可用区部署

支持单可用区部署，三个节点自动部署到不同的机架的物理机上，可以提供跨机架的高可用。

### 多可用区部署

支持多可用区部署，您可指定主从节点与隐藏节点部署的可用区，可以提供跨机房的高可用。

## 安全保障
 
### VPC 私有网络
实例部署在用户自定义的 VPC 私有网络内，在 TCP 层直接进行网络隔离保护，确保数据安全性。

### 白名单
支持用户自定义IP白名单，从访问源进行安全控制。


## 备份与恢复

### 自动备份
每天自动全量备份数据并保留7天，备份文件以三副本的方式存放在云存储。

### 手动备份
支持即时手动创建备份，备份数据长期保存。

### 数据恢复
支持一键恢复备份数据至当前实例；此外，基于增量备份，支持根据七天内任意时间点的数据创建新的数据库实例。

## 监控报警

### 可视化监控
MongoDB 控制台提供丰富的监控信息，包括CPU、内存、存储空间、IOPS等信息，您可以随时查看实例运行状态。

### 自动报警
您可以根据监控项设置报警规则，当监控项达到设置的阈值时，系统会通过短信和邮件的方式向您发送报警信息。

## 相关参考

- [产品概述](../Introduction/Product-Overview.md)
- [产品规格](../Introduction/Specifications.md)
- [价格总览](../Pricing/Price-Overview.md)
- [创建实例](../Getting-Started/Create-Instance.md)
- [变更配置](../Operation-Guide/Instance-Management/Modify-Instance-Spec.md)
- [数据恢复](../Operation-Guide/Backup/Restore-Instance.md)
- [设置报警规则](../Operation-Guide/Monitoring/Alarm-Rules.md)


