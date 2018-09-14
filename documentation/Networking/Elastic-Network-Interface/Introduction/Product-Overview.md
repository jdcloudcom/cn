# 产品概述

弹性网卡是一种虚拟网络接口，您可以在云主机上绑定弹性网卡以使云主机接入不同网络。弹性网卡可以在构建业务流量分离、多业务承载以及网络高可用等应用场景时提供支持。京东云弹性网卡为地域级属性弹性网卡，弹性网卡可以绑定私有网络内任意可用区云主机。每台云主机可以绑定多块弹性网卡，绑定数量依据云主机实例规格而定。

弹性网卡主要具备以下特性：

* 多网卡多IP：依据云主机实例规格，京东云每台云主机可以绑定多块弹性网卡，每块弹性网卡可以分配多个内网IP地址，同时，每个内网IP地址可以关联一个弹性公网IP地址。

* 弹性插拔：京东云弹性网卡为地域级属性弹性网卡，可以绑定私有网络内任意可用区云主机。在发生故障时，弹性网卡可以从故障云主机上解绑，并迁移至另一台备用云主机。

* 业务安全：京东云每台云主机可挂载多块弹性网卡，特定业务流量可由特定弹性网卡承载。不同弹性网卡可独立关联安全组，分别应用不同的安全组策略，从而提升业务流量安全性。

* 路由控制：京东云每台云主机可挂载同一私有网络内不同子网的弹性网卡，每个子网可以分别设置访问控制策略以及路由转发策略，配合云主机内部路由配置工具，可实现对于网络流量的精确控制。

## 常用操作

- 弹性网卡管理
	- [创建弹性网卡](../Operation-Guide/Elastic-Network-Interface-Management/Create-Elastic-Network-Interface.md)
	- [删除弹性网卡](../Operation-Guide/Elastic-Network-Interface-Management/Delete-Elastic-Network-Interface.md)
	- [绑定弹性网卡](../Operation-Guide/Elastic-Network-Interface-Management/Associate-Elastic-Network-Interface.md)
	- [解绑弹性网卡](../Operation-Guide/Elastic-Network-Interface-Management/Disassociate-Elastic-Network-Interface.md)
	- [启用随实例删除](../Operation-Guide/Elastic-Network-Interface-Management/Enable-Delete-with-VM.md)
	- [取消随实例删除](../Operation-Guide/Elastic-Network-Interface-Management/Disable-Delete-with-VM.md)
- 内网IP管理
	- [分配内网IP](../Operation-Guide/Private-IP-Management/Assign-Secondary-IP.md)
	- [释放内网IP](../Operation-Guide/Private-IP-Management/Unassign-Secondary-IP.md)
	- [绑定公网IP](../Operation-Guide/Private-IP-Management/Associate-Elastic-IP.md)
	- [解绑公网IP](../Operation-Guide/Private-IP-Management/Disassociate-Elastic-IP.md)
- 安全组管理
	- [添加安全组](../Operation-Guide/Security-Group-Management/Associate-Security-Group.md)
	- [移除安全组](../Operation-Guide/Security-Group-Management/Disassociate-Security-Group.md)
- 云主机配置
	- [Linux系统临时配置](../Operation-Guide/VM-Configuration/Linux-Temporary-Configuration.md)
	- [Linux系统永久配置](../Operation-Guide/VM-Configuration/Linux-Permanent-Configuration.md)

## 计费
弹性网卡服务免费，弹性网卡关联的弹性公网IP独立计费。详细说明请参见：[计费说明](../Pricing/Billing-Overview.md)。
