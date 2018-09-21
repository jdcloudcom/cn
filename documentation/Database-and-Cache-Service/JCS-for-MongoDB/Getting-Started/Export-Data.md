# 导出数据

云数据库 MongoDB 提供自动备份与手动备份功能。如需导出数据，您可以下载备份文件后导出到本地数据库。

## 操作步骤
1. 登录 [MongoDB 控制台](https://mongodb-console.jdcloud.com/mongodb)。
2. 在“实例列表”页面，选择目标实例，点击 **实例名称** ，进入“实例详情”页面。
3. 在“实例详情”页面，点击 **备份与恢复** ，查看备份数据。

   ![查看备份](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-010.png)
   
4. 选择要下载的备份，在操作项中，点击 **下载** ，打开下载弹窗。

   ![查看备份](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-009.png)
	
5. 下载备份文件到本地。
	
	说明
	- 内网地址和外网地址有效期为24小时；
	- 使用wget下载时需要对URL添加英文引号；
	- 若云主机与云数据库在同一地域，建议您采用内网地址下载；
		
6. 将备份文件导入到本地数据库。

   > mongorestore --host xxx --port=27017 --authenticationDatabase admin --archive=xxx(文件路径)  --gzip -u root -p xxx

## 相关参考

- [导入数据](Import-Data.md)
