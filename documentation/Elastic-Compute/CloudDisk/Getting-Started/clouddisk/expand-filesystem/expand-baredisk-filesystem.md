# 扩容裸盘文件系统（Linux）

<br>

如果之前并未对硬盘执行过分区操作，可以参考如下方法，直接对硬盘文件系统进行扩容：

1.在控制台完成云硬盘[升级容量](https://www.jdcloud.com/help/detail/508/isCatalog/1)操作；

2.执行[挂载云硬盘](https://www.jdcloud.com/help/detail/505/isCatalog/1)，确保云硬盘处于“已挂载”状态；

3.使用fdisk -l 查看硬盘分区信息；


![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/expand-filesystem/epand_bare_001.jpg)

4.使用df -h查看挂载信息；



![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/expand-filesystem/epand_bare_002.jpg)


5. 执行umount操作取消挂载；




![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/expand-filesystem/epand_bare_003.jpg)

6.执行e2fsck -f /dev/vdb检测文件系统正确性；




![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/expand-filesystem/epand_bare_004.jpg)


7.执行resize2fs /dev/vdb重新定义文件系统大小；




![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/expand-filesystem/epand_bare_005.jpg)


8. 执行mount /dev/vdb /mnt重新挂载磁盘，可以看到磁盘已经扩容成功。




![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/expand-filesystem/epand_bare_006.jpg)

	




	
	


