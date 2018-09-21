# 创建云硬盘

<br>

##  操作说明


- 您可以创建云硬盘并将其挂载到同一地域或同一可用区内的任何云主机上；



- 一台云主机最多可挂载8块云硬盘；



- 每块SSD云盘最大支持1000G容量；每块高效云盘最大支持3000G容量；



- 如您需要在新硬盘中保留某一云硬盘的历史数据，可以使用某个云硬盘的快照创建新盘，请参考[使用快照创建](https://www.jdcloud.com/help/detail/891/isCatalog/1)；



- 开通按配置计费云硬盘，请确保您的账户余额不少于 50元。

<br>

##  操作指南

1、打开[京东云控制台](https://console.jdcloud.com/)，选择【弹性计算】-【云主机】-【云硬盘】；

2、点击云硬盘列表上方的【创建】按钮，开始云硬盘创建流程；

3、选择云硬盘付费类型，包年包月或按配置；

4、选择硬盘所在地域和可用区；

5、选择云硬盘类型及容量；

注：云硬盘必须挂载到同一可用区内的云主机上，不支持跨地域、跨可用区挂载；

<br>

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/cloud-disk-001.jpg)

<br>

6、输入云硬盘名称及描述；

注： 也可在云硬盘创建页面单击【[使用快照创建](https://www.jdcloud.com/help/detail/891/isCatalog/1)】，基于快照创建新的云硬盘；

<br>

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/cloud-disk-002.png)

<br>

7、包年包月的用户请选择购买时长及数量；按配置购买的用户只需选择购买数量；

<br>

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/cloud-disk-003.png)

<br>


8、确认已选配置无误后，点击【立即购买】进入订单确认页。选择包年包月计费类型在订单确认页核对资源信息后，点击“去支付”进入确认支付页，支付成功后即可触发资源创建。选择按配置计费类型在订单确认页点击“确认开通”即可触发资源创建。

9、支付成功后即可进入控制台查看已创建的云硬盘。

**注意事项**：



- 云硬盘可在同一地域或可用区内任意云主机间自由挂载、卸载；



- 单次最多可创建10块云硬盘；


## 下一步



- **Linux**

对于 Linux 系统，购买云盘之后，您需要进行挂载、分区、格式化、之后才能在系统中看到并使用。

1、挂载数据盘，请参见[挂载云硬盘](https://www.jdcloud.com/help/detail/505/isCatalog/1)。<br>

2、对挂载的磁盘进行分区格式化和挂载新分区的操作，请参见 [Linux分区、格式化和创建文件系统](https://www.jdcloud.com/help/detail/515/isCatalog/1)。




- **Windows**

对于 Windows 系统，购买云盘之后，您需要进行挂载、格式化之后才能使用。

1、挂载数据盘，请参见 [挂载云硬盘](https://www.jdcloud.com/help/detail/505/isCatalog/1)。<br>

2、对挂载的磁盘进行格式化，请参见 [Windows分区、格式化和创建文件系统](https://www.jdcloud.com/help/detail/514/isCatalog/1)。

	

	




	
	


