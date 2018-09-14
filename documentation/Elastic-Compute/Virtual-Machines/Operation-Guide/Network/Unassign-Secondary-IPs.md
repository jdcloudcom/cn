# 释放辅助内网IP

## 操作步骤

1. 访问[云主机控制台](https://cns-console.jdcloud.com/host/compute/list)，即进入实例列表页面。或访问[京东云控制台](https://console.jdcloud.com)点击左侧导航栏【弹性计算】-【云主机】进入实例列表页。
2. 选择地域。
3. 在实例列表中选择需要释放辅助内网IP的实例，点击名称进入详情页。
4. 点击【弹性网卡】Tab，选择需要释放IP的弹性网卡，找到需要释放的辅助内网IP，点击【释放】按钮。
5. 在弹出二次确定弹窗中，点击【确定】。

		请注意：主内网IP不支持释放。辅助内网IP释放时会自动解绑其绑定的弹性公网IP，若您需要删除该弹性公网IP，请至弹性公网IP列表页进行操作。

此外您还可以从弹性网卡控制台进行释放操作，详细步骤请参见[弹性网卡侧释放辅助IP](../../../../Networking/Elastic-Network-Interface/Operation-Guide/Private-IP-Management/Unassign-Secondary-IP.md)。


## 相关参考

[弹性网卡侧释放辅助IP](../../../../Networking/Elastic-Network-Interface/Operation-Guide/Private-IP-Management/Unassign-Secondary-IP.md)

[删除弹性公网IP](../../../../Networking/Elastic-IP/Operation-Guide/Elastic-IP-Management/Delete-Elastic-IP.md)