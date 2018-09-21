# 下载备份文件

MongoDB 实例的备份文件支持下载，您可以根据需要自行下载备份文件。

## 操作步骤：
1. 登录 [MongoDB 控制台](https://mongodb-console.jdcloud.com/mongodb)。
1. 在"实例列表"页面，选择目标实例，点击 **实例名称**，进入"实例详情"页面。
1. 在"实例详情"页面，点击 **备份与恢复**， 查看备份数据。
1. 选择要下载的备份，在操作项中，点击 **下载**，打开"下载弹窗"。
	
   ![](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-020.png)

1. 下载备份文件到本地。

	说明
	
	- 内网地址和外网地址有效期为24小时；
	- 使用wget下载时需要对URL添加英文引号；
	- 若云主机与云数据库在同一地域，建议您采用内网地址下载；

## 相关参考

- [手动创建备份](Create-Backup.md)
- [根据备份创建实例](Create-Instance-by-Backup.md)
- [根据时间点创建实例](Create-Instance-by-Point-in-Time.md)
- [设置自动备份](Modify-Backup-Policy.md)
- [数据恢复](Restore-Instance.md)
