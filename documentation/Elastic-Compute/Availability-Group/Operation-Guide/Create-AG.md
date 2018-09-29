# 创建高可用组

## 前置条件

创建高可用组前您需要先完成[创建实例模板](../../Virtual-Machines/Operation-Guide/Instance-Template/Create-Instance-Template.md)。

## 操作步骤

1. 访问[高可用组控制台](https://cns-console.jdcloud.com/availabilitygroup/list)，即进入高可用组列表页面。或访问[京东云控制台](https://console.jdcloud.com)点击左侧导航栏【弹性计算】-【高可用组】进入高可用组列表页。
2. 选择地域。
3. 点击【创建】，进入高可用组创建页面。
4. 选择地域：在此步骤仍可以选择新建高可用组对应的地域。如果所选地域限额已满，可以通过提交工单提升限额。
5. 设置高可用组的可用区属性，为保障最优的业务可用性，建议选择多可用区。高可用组内云主机将在高可用组内均匀分布，降低当单个可用区出现物理故障时对您业务的影响。
6. 设置高可用组名称及描述，如：Web服务高可用组。
7. 选择实例模板，下拉框将列出当前地域下满足条件的实例模板，请注意需选择配置了第二代云主机规格的实例模板，此处选择上一步创建的“Web服务实例模板”。
8. 点击【确定】触发创建高可用组，您将在高可用组列表页看到创建成功的高可用组。

		请注意：高可用组创建完成后不可修改可用区信息。


## 相关参考

[创建实例模板](../../Virtual-Machines/Operation-Guide/Instance-Template/Create-Instance-Template.md)
