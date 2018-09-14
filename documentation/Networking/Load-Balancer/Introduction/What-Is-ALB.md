# 产品概述


负载均衡可将大并发流量分发到多台后端实例，调整资源利用情况，消除由于单台设备故障对系统的影响，提高系统可用性、扩展系统服务能力。 

负载均衡具备以下特性：

* 流量分发：负载均衡服务通过设置虚拟服务地址VIP，将相同VPC下的后端实例（云主机/容器）虚拟为一个服务资源池，可将前端客户的访问流量按照指定的规则分发至后端服务资源池进行处理，提升用户对外服务能力。
* 多种协议侦听：负载均衡支持TCP/HTTP/HTTPS等多种协议的不同端口侦听服务，以支持丰富多样的客户端服务接入和流量分发。
* 自动健康检查：负载均衡服务会检查后端服务资源池中实例的健康状态，自动隔离、挂载后端提供服务的实例，消除设备单点故障，保障业务正常运行。
* 自动调节后端实例数：负载均衡后端可以绑定指定的高可用组，通过设置弹性伸缩策略，自动调整后端服务实例数量，合理配置资源。
* 防DDoS攻击：提供基于公网IP的抗DDoS攻击能力，提升了服务的安全性能。
* 会话保持：负载均衡支持基于HTTP/HTTPS协议类型的会话保持功能。
* 空闲连接超时：负载均衡支持基于TCP/HTTP/HTTPS协议的空闲连接超时。
* 源IP透传：负载均衡支持基于TCP/HTTP/HTTPS协议的客户端IP透传功能。

## 常用操作

- 快速上手
	- [创建实例](../Getting-Started/Create-Instance.md)
	- [设置白名单](../Getting-Started/Set-Whitelist.md)
	- [连接实例](../Getting-Started/Connect-Instance.md)
- 数据迁移
	- [将数据导入到云](../Getting-Started/Import-Data.md)
	- [从云导出数据](../Getting-Started/Export-Data.md)
- 扩容升级
	- [变更实例规格](../Operation-Guide/Instance-Management/Modify-Instance-Spec.md)
- 备份与恢复
	- [设置自动备份策略](../Operation-Guide/Backup/Modify-Backup-Policy.md)
	- [手动创建备份](../Operation-Guide/Backup/Create-Backup.md)
	- [数据恢复](../Operation-Guide/Backup/Restore-Instance.md)
- 运维管理
	- [查看监控信息](../Operation-Guide/Monitoring/Monitoring.md)
	- [设置报警规则](../Operation-Guide/Monitoring/Alarm-Rules.md)

## 计费
目前使用负载均衡产品不收费，如绑定了公网IP资源，需单独支付公网IP费用，详见[公网IP价格](https://www.jdcloud.com/help/detail/1579/isCatalog/1)。