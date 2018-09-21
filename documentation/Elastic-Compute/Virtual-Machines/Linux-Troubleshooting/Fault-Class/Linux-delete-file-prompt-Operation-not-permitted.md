# Linux删除文件提示Operation not permitted

**问题现象:**

用户在云主机内对文件做删除,移动等操作，会提示"Operation not permitted"错误，无法操作成功，如下图；

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E5%88%A0%E9%99%A4%E6%96%87%E4%BB%B6%E6%8F%90%E7%A4%BAOperation%20not%20permitted01.png)


**问题原因:**

相关文件被添加了 i 保护属性导致操作失败。


**处理方法：**

使用*lsattr*命令查看文件属性，可以看到文件被添加了 i 的属性；此属性表示文件不可被修改，也无法删除；

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E5%88%A0%E9%99%A4%E6%96%87%E4%BB%B6%E6%8F%90%E7%A4%BAOperation%20not%20permitted02.png)


使用*chattr*命令将i属性删除；

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E5%88%A0%E9%99%A4%E6%96%87%E4%BB%B6%E6%8F%90%E7%A4%BAOperation%20not%20permitted03.png)

将i属性删除后，在操作此文件便会正常；
