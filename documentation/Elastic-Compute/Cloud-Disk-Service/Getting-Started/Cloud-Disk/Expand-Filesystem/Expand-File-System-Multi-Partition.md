# 扩容文件系统（多分区）

<br>

## 扩容Windows系统多分区的云硬盘

以Windows Server 2012 R2 标准版 64位为例，将云主机已挂载的云硬盘由20G扩容到40G。

1、打开Windows服务器管理器，进入磁盘管理页面：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/expand-filesystem/expand_multipart_001.jpg)


2、在需要进行扩容的分区上点击右键，然后选择扩展卷，按照向导进行扩容即可。


![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/expand-filesystem/expand_multipart_002.jpg)

**扩容Linux系统多分区的云硬盘**

以CentOS 7.2 64位为例，将云主机已挂载的云硬盘由40G扩容到50G。

**注：执行扩容操作之前，请确保待扩容分区处于卸载状态。执行步骤参考扩容文件系统（Linux）**。

1、执行 fdisk /dev/vdc（请使用待扩容磁盘设备名替换vdc）。删除需要扩容的磁盘分区后重新执行磁盘分区操作。



![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/expand-filesystem/expand_multipart_003.jpg)


2、对指定的磁盘分区执行 e2fsck 和 resize2fs 操作，完成文件系统扩容：


![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/expand-filesystem/expand_multipart_004.jpg)

<br>

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/expand-filesystem/expand_multipart_005.jpg)



	
	


