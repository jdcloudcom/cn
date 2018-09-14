# 根据备份创建实例

MongoDB 控制台提供了根据备份创建实例的功能，您可以根据某一实例的备份文件创建新的实例。

## 注意事项

- 新实例创建过程中请勿删除使用的备份问题，否则会创建失败。
- 新实例所在地域只能与源实例地域一致。

## 操作步骤

1. 登录 [MongoDB 控制台](https://mongodb-console.jdcloud.com/mongodb)。
1. 在“实例列表”页面，选择目标实例，点击 **实例名称**，进入“实例详情”页面。
1. 在“实例详情”页面，点击 **备份与恢复**， 查看备份数据。
1. 选择要使用的备份，在操作项中点击 **根据备份创建**，进入根据备份创建实例页面。

   ![](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-022.png)

	
1. 在根据备份创建实例页面，选择计费类型、实例规格配置等信息，完成实例创建。创建过程同 [创建实例](https://github.com/jdcloudcom/cn/blob/master/documentation/Cloud-Database-and-Cache/MongoDB/Getting-Started/CreateInstance.md) 。

   注意：地域与源实例所在地域一致，不可修改。

   ![](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-023.png)

## 相关参考

- [手动创建备份](Create-Backup.md)
- [下载备份文件](Download-Bckup.md)
- [根据时间点创建实例](Create-Instance-by-Point-in-Time.md)
- [设置自动备份](Modify-Backup-Policy.md)
- [数据恢复](Restore-Instance.md)
