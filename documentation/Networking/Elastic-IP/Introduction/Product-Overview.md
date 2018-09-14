# 产品概述

弹性公网IP是可以独立申请的公网IP地址，支持与云主机、容器、负载均衡、NFV实例等资源进行动态绑定和解绑。弹性公网IP的主要作用是屏蔽实例故障，通过手动配置的方式，当实例出现故障时弹性公网IP可以漂移到冗余实例上，从而达到快速响应故障的目的。

京东云目前采用业内领先的双活vRouter（Virtual Router，虚拟路由器）高可用技术，相对于传统的主备vRouter高可用方式，该技术在高并发连接、超大流量负载以及流量突发等场景下可以为用户提供链路冗余以及高可用性。基于该项技术，京东云弹性公网IP最大带宽可以达到用户实际购买带宽的150%，为用户业务提供保障。

基于双活vRouter的流量分担模型，普遍情况下，弹性公网IP的最大带宽为用户实际购买带宽的150%；在极特殊情况下，如单连接FTP下载文件，弹性公网IP最大带宽约为用户实际购买带宽的75%。

弹性公网IP主要具备以下特性：

* 完全弹性：京东云提供的公网IP全部为弹性公网IP。无论您是独立购买弹性公网IP，或是在购买云主机等其它资源时一并购入弹性公网IP，均可以随时更改弹性公网IP与云资源的绑定关系。

* 支持多种资源绑定：弹性公网IP支持与云主机、容器、负载均衡、NFV实例等云资源进行绑定，为云资源提供公网访问能力。

* 支持多种计费类型：弹性公网IP支持包年包月、按配置和按用量三种计费类型，用户可根据实际业务需求选择合适的计费类型。

* 带宽灵活调整：弹性公网IP支持带宽调整，用户可根据业务流量需求变化随时更改带宽，修改即时生效。

## 常用操作

- 弹性公网IP管理
	- [创建弹性公网IP](../Operation-Guide/Elastic-IP-Management/Create-Elastic-IP.md)
	- [删除弹性公网IP](../Operation-Guide/Elastic-IP-Management/Delete-Elastic-IP.md)
	- [绑定弹性公网IP](../Operation-Guide/Elastic-IP-Management/Associate-Elastic-IP.md)
	- [解绑弹性公网IP](../Operation-Guide/Elastic-IP-Management/Disassociate-Elastic-IP.md)
	- [修改弹性公网IP带宽](../Operation-Guide/Elastic-IP-Management/Modify-Elastic-IP.md)
- 弹性公网IP资源信息查看
	- [弹性公网IP资源信息查看](../Operation-Guide/View-Elastic-IP-Detail/View-Elastic-IP-Detail.md)
- 弹性公网IP监控信息查看
	- [弹性公网IP监控信息查看](../Operation-Guide/View-Elastic-IP-Monitoring/View-Elastic-IP-Monitoring.md)
- 弹性公网IP计费信息查看
	- [弹性公网IP计费信息查看](../Operation-Guide/View-Elastic-IP-Billing/View-Elastic-IP-Billing.md)
- 导出弹性公网IP列表
	- [导出弹性公网IP列表](../Operation-Guide/Export-Elastic-IP-List/Export-Elastic-IP-List.md)

## 计费
弹性公网IP支持包年包月、按配置和按用量计费三种计费类型。详细说明请参见：[计费说明](../Pricing/Billing-Overview.md)。
