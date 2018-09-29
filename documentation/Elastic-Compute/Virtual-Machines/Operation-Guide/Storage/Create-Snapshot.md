# 创建云硬盘快照

快照可保留某个时间点上云硬盘内数据状态，可作为数据备份。
## 使用限制

* 默认单用户单个地域快照的配额为15个，可以通过提交工单提升限额；
* 为保证数据完整性，请您在创建快照之前，停止对云硬盘进行写入操作，以保证快照数据的完整性；
* 建议您在制作快照前先对云硬盘进行卸载操作，创建快照后再重新挂载至实例，请查阅[卸载云硬盘](Detach-Cloud-Disk.md)、[挂载云硬盘](Attach-Cloud-Disk.md)；

## 操作步骤
详细操作步骤请参考云硬盘侧[创建云硬盘快照](http://docs.jdcloud.com/cn/cloud-disk-service/create-clouddisk-snapshot)。
 	
 	请注意：第一次创建快照为全量快照所需时间取决于云硬盘容量的大小，云硬盘容量越大耗时越长，还请耐心等待。
 	
 	
## 相关参考

[卸载云硬盘](Detach-Cloud-Disk.md)

[挂载云硬盘](Attach-Cloud-Disk.md)

[创建云硬盘快照](http://docs.jdcloud.com/cn/cloud-disk-service/create-clouddisk-snapshot)