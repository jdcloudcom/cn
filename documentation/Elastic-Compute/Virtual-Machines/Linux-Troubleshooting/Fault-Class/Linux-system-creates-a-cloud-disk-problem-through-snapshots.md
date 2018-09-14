# Linux系统通过快照创建云硬盘问题



使用云硬盘快照购买创建的云硬盘，如果新盘创建时空间大小选择是大于原快照磁盘空间大小的，那么创建磁盘后默认空间大小是和原盘一致的，uuid也相同，如图：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9F%E9%80%9A%E8%BF%87%E5%BF%AB%E7%85%A7%E5%88%9B%E5%BB%BA%E4%BA%91%E7%A1%AC%E7%9B%98%E9%97%AE%E9%A2%9801.png)

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9F%E9%80%9A%E8%BF%87%E5%BF%AB%E7%85%A7%E5%88%9B%E5%BB%BA%E4%BA%91%E7%A1%AC%E7%9B%98%E9%97%AE%E9%A2%9802.png)

需要对新盘进行扩容操作，才可以扩展为购买创建的空间大小。以新盘为/dev/vdd 为例。

1.卸载新云硬盘。

*umount /dev/vdd*

2.重新对磁盘进行分区操作。

*fdisk /dev/vdd*

依次键入p d n p 1 两次回车 wq


p: 打印分区信息

d: 删除分区

n: 新建分区

p: 新建分区的类型为主分区

1: 分区号为1

wq: 保存并退出

**注：保存之前请确定自己的操作无误，若发现有误操作，可键入q直接退出，此前操作都将无效。**

3.对新盘进行文件扩展操作。执行：

*e2fsck -f /dev/vdd1*

*resize2fs /dev/vdd1*

之后挂载mount /dev/vdd1，df -h查看磁盘大小即正常。

如无法解决您的问题，请向我们提工单。
