# 使用快照创建

<br>

##  操作说明

您可以使用快照创建云硬盘并将其挂载到同一地域或同一可用区内的任何一台云主机上。使用快照创建的云硬盘初始状态保留了快照的全部数据，将使用快照创建的云硬盘挂载到云主机之后，您可以对快照保留的所有数据进行读写操作。

- 为保证数据可用性，新建云硬盘的最小可选容量与快照容量相同；



- 每块SSD云盘最大支持1000G容量；每块高效云盘最大支持3000G容量；



- 基于快照创建云硬盘，需要经历从对象存储恢复数据至云硬盘的过程，因此要比创建新硬盘多花费一些时间，请您耐心等待。



<br>

##  操作指南

**注**：您应已经给当前地域下的云硬盘创建了快照

**方法一：您可以在创建云硬盘页面，直接选择【使用快照创建】：**

1、打开[京东云控制台](https://console.jdcloud.com/)，选择【弹性计算】-【云主机】-【云硬盘】；

2、点击云硬盘列表页上的【创建】按钮，跳转到云硬盘创建页面，开始云硬盘创建流程；

<br>

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/cloud-disk-004.png)

<br>

3、选择云硬盘付费类型，包年包月或按配置购买；

4、点击基本信息栏中的【使用快照创建】；

5、在弹出的【根据快照创建】页面中，选择所需快照后点击【确定】；

<br>

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/cloud-disk-005.png)

<br>

6、选择云硬盘容量；

**注**：

1）默认创建与快照源硬盘类型及容量大小相同的云硬盘，且硬盘类型不能修改；

2）新硬盘容量大小支持修改，最小容量同快照大小，最大容量受硬盘类型限制；


<br>

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/cloud-disk-006.jpg)

<br>

7、包年包月的用户请选择购买时长及数量；按配置购买的用户只需选择购买数量；

8、确认已选配置无误后，点击【立即购买】进入订单确认页。选择包年包月计费类型在订单确认页核对资源信息后，点击“去支付”进入确认支付页，支付成功后即可触发资源创建。选择按配置计费类型在订单确认页点击“立即开通”即可触发资源创建。

9、支付成功后即可进入控制台查看已创建的云硬盘。

**方法二：您也可以在云硬盘快照列表页面，直接选择某一快照，进入使用快照创建页面：**

1、打开[京东云控制台](https://console.jdcloud.com/)，选择【弹性计算】-【云主机】-【云硬盘快照】；

2、在云硬盘快照列表中选择需要获取其数据的云硬盘快照，点击右侧的【根据快照创建】按钮，进入基于快照创建云硬盘流程；

<br>

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/cloud-disk-007.png)

<br>


3、选择新建云硬盘的付费类型、规格、数量等配置，确认已选配置无误后点击【立即购买】完成支付后即可进入控制台查看已创建的云硬盘；

<br>

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/cloud-disk-008.jpg)

<br>
