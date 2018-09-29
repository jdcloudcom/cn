# 绑定弹性网卡

弹性网卡主要具有以下关联信息：

* 主网卡 ：一种特殊类型的弹性网卡，随云主机一同创建生成，生命周期与云主机相同
* 辅助网卡：需独立创建，与删除，支持弹性插拔其中主网卡不支持绑定和解绑，辅助网卡支持绑定解绑
* 主内网 IP： 弹性网卡创建时分配的首个内网IP地址，可由用户指定或系统分配，不支持释放
* 辅助内网 IP： 弹性网卡分配的除主IP以外的其它内网IP地址，可由用户指定或系统分配，支持释放
* 弹性公网 IP： 弹性公网IP是一种可独立申请的公网IP地址，可以与内网IP灵活绑定与解绑
* 安全组： 一种分布式且有状态的防火墙，用于对进出弹性网卡的流量进行过滤
* MAC 地址： MAC地址是弹性网卡的唯一标识符

## 前提条件

* 实例需要处于“运行中”或“已停止”状态；
* 实例已绑定弹性网卡数不可超过可绑定上限则无法绑定额外的弹性网卡；
* 仅支持将同VPC的弹性网卡绑定至实例。

根据不同实例规格对应的配置不同，实例可绑定弹性网卡数及单块弹性网卡可分配内网IP数不同，详细情况如下表。

|vCPU数|可绑定弹性网卡数|单网卡可分配内网IP数
|:---|:---|:---|
1核-2核	|2	|21
4核-8核	|4	|21
8核以上	|8	|21

## 操作步骤

1. 访问[云主机控制台](https://cns-console.jdcloud.com/host/compute/list)，即进入实例列表页面。或访问[京东云控制台](https://console.jdcloud.com)点击左侧导航栏【弹性计算】-【云主机】进入实例列表页。
2. 选择地域。
3. 在实例列表中选择需要绑定弹性网卡的实例，点击名称进入详情页。
4. 点击【弹性网卡】Tab-【绑定弹性网卡】按钮。
5. 在弹出弹窗中，选择一个弹性网卡，点击【确定】。
		
		请注意：
		* 操作绑定后需要几分钟生效，还请耐心等待后刷新页面。
		* 操作绑定弹性网卡需要实例处于运行或停止状态。
		* 绑定后需要登录实例进行相关路由及IP配置。
		
详细路由及IP配置请参见[配置路由](../../../../Networking/Elastic-Network-Interface/Operation-Guide/VM-Configuration/Linux-Permanent-Configuration.md)。

此外您还可以从弹性网卡控制台进行绑定操作，详细步骤请参见[弹性网卡侧绑定弹性网卡](../../../../Networking/Elastic-Network-Interface/Operation-Guide/Elastic-Network-Interface-Management/Associate-Elastic-Network-Interface.md)。

## 相关参考

[配置路由](../../../../Networking/Elastic-Network-Interface/Operation-Guide/VM-Configuration/Linux-Permanent-Configuration.md)

[弹性网卡侧绑定弹性网卡](../../../../Networking/Elastic-Network-Interface/Operation-Guide/Elastic-Network-Interface-Management/Associate-Elastic-Network-Interface.md)