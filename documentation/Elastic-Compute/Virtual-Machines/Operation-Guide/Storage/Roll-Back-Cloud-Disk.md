# 使用快照恢复云硬盘
对云硬盘制作快照后，如果当前系统出现问题，您希望某块云硬盘数据能恢复至之前的某一时刻，您可通过恢复云硬盘实现。详细操作步骤请参考云硬盘侧[恢复云硬盘](http://docs.jdcloud.com/cn/cloud-disk-service/recover-clouddisk)。

## 操作限制

* 仅可对创建快照的源云硬盘进行恢复；
* 源云硬盘未被删除；
* 源云硬盘需为未挂载状态，若云硬盘已挂载至实例还请操作[卸载云硬盘](Detach-Cloud-Disk.md)；
* 操作恢复云硬盘后，从创建快照时刻至当前时刻时间内数据均会丢失，请谨慎操作；
* 若创建快照后云硬盘有进行过扩容操作，将恢复后的云硬盘挂载至实例时，需要您重新登录实例进行[扩容文件系统](http://docs.jdcloud.com/cn/cloud-disk-service/cloud-disk-expansion-overview)。

## 相关参考
[恢复云硬盘](http://docs.jdcloud.com/cn/cloud-disk-service/recover-clouddisk)

[卸载云硬盘](Detach-Cloud-Disk.md)

[扩容文件系统](http://docs.jdcloud.com/cn/cloud-disk-service/cloud-disk-expansion-overview)

