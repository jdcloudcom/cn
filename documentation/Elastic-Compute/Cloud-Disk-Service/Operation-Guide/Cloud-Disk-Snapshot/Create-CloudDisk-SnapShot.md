# 创建云硬盘快照

<br>

##  操作说明

快照是京东云提供的数据备份方式。快照保留了某个指定时间点之前云硬盘上的所有数据，且不占用用户的存储空间。



- 同一地域下单用户快照的配额为15块；



- 为保证数据完整性，请您在创建快照之前，停止对云硬盘进行写入操作，以保证快照数据的完整性；



- 在执行创建快照前，建议您对云硬盘进行卸载操作，创建快照后再重新挂载到云主机上；



- 手动快照的生命周期独立于云硬盘，请您及时删除不需要的快照；



- 创建快照所需时间取决于云硬盘容量的大小，云硬盘容量越大耗时越长；

<br>

##  操作指南

### 方法一：在云硬盘列表页创建快照

1、打开[京东云控制台](https://console.jdcloud.com/)，选择【弹性计算】-【云主机】-【云硬盘】；

2、进入京东云控制台云硬盘列表页，选择需要制作快照的云硬盘，点击操作列【制作快照】按钮，在弹出的制作快照窗口，输入快照名称、描述，点击【确认】后开始创建快照。

3、快照制作完成，则相关信息更新。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/Create-CloudDisk-SnapShot/create-snapshot-001.jpg)
<br>
### 方法二：在云硬盘详情页创建快照


1、打开[京东云控制台](https://console.jdcloud.com/)，选择【弹性计算】-【云主机】-【云硬盘】；

2、进入云硬盘列表页后找到需要制作快照的云硬盘，点击对应云硬盘名称跳转到其详情页面；

3、点击右上角【操作】-【制作快照】按钮，弹出制作快照窗口；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/Create-CloudDisk-SnapShot/create-snapshot-002.jpg)

4、输入快照名称、描述，点击【确认】后开始为云硬盘创建快照；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/Create-CloudDisk-SnapShot/create-snapshot-003.jpg)

5、快照制作完成，则相关信息更新。





	

	




	
	


