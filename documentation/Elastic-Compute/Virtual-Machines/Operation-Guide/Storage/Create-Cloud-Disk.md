# 创建云硬盘

京东云为您提供多种创建云硬盘方法：

* 实例创建时一起创建云硬盘，详细请参考[创建实例](../Instance/Create-Instance.md)；
* 单独[创建云硬盘](http://docs.jdcloud.com/cn/cloud-disk-service/create-cloud-disk)；
* [使用快照创建云硬盘](http://docs.jdcloud.com/cn/cloud-disk-service/create-disk-by-snapshot)，即可在新硬盘中保留某一云硬盘的历史时间点数据。

请注意：

* 默认每个地域云硬盘限额为15块，可以通过提交工单提升限额；
* 单实例可以支持最多挂载8块云硬盘；
* 每块SSD云盘最大支持1000G容量；每块高效云盘最大支持3000G容量；
* 若您需要创建按配置计费云硬盘，您需要保证您的余额加可用代金券不低于50元，若当前余额不足请进行充值；
* 目前实例不支持合并多块云硬盘。云盘创建后，每块云硬盘都是独立个体，无法通过格式化将多块云硬盘空间合并到一起。建议您提前做好磁盘数量和容量的规划；若云硬盘已经创建，但您需要对其进行扩容，可按以下步骤操作：
	* 包年包月云硬盘，通过扩容云硬盘实现；
	* 按配置计费的云硬盘，您可对其创建云硬盘快照，再使用快照创建新盘，旧盘即可删除。

## 相关参考
[创建实例](../Instance/Create-Instance.md)

[创建云硬盘](http://docs.jdcloud.com/cn/cloud-disk-service/create-cloud-disk)

[使用快照创建云硬盘](http://docs.jdcloud.com/cn/cloud-disk-service/create-disk-by-snapshot)