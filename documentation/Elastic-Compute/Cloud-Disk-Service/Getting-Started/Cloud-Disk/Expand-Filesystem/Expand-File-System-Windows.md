# 扩容文件系统（Windows）

<br>

以windows Server R2 2008标准版为例，假设云主机上已挂载一块 320GB 的硬盘，现在需要扩容到 330GB 。具体步骤如下：

1、打开Windows服务器管理器，进入磁盘管理页面，找到需要进行扩容操作的磁盘：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/expand-filesystem/windows_expand_001.jpg)

2、右键单击需要进行扩容操作的磁盘空间，在弹出的菜单中选择“扩展卷”：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/expand-filesystem/windows_expand_002.jpg)


3、在弹出的扩展卷向导中选择新增的磁盘空间后，点击“下一步”：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/expand-filesystem/windows_expand_003.jpg)

4、确认新增的磁盘空间大小后，点击“完成”按钮，完成文件系统扩容操作：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/expand-filesystem/windows_expand_004.jpg)

5、返回服务器管理器->磁盘管理页面，确认文件系统已扩容完成：


![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/expand-filesystem/windows_expand_005.jpg)







	
	


