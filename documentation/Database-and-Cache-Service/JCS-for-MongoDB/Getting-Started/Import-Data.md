# 导入数据

通过MongoDB自带的mongodump和mongorestore命令，您可以将自建 MongoDB 数据库的数据导入到云数据库 MongoDB 实例 。

## 注意事项
请使用MongoDB3.2以上版本的mongodump和mongorestore工具。

## 操作步骤
1. 通过 mongodump 命令备份自建数据库数据。

	连接自建数据库，选用相应权限的账号，执行 mongodump 将自建数据库内容导出。例如，执行以下语句导出所有数据库，默认生成文件名为dump的备份文件。

	> mongodump --host xxx:27017 --authenticationDatabase  admin -u xxx -p xxx

2. 通过 mongostore 命令将备份出的文件导入至云数据库 MongoDB。
	根据上一步导出生成的备份文件，执行 mongostore 命令将数据全部导入至云数据库MongoDB。例如，执行以下语句将数据库全部导入。

	> mongorestore --host dds-xxx:3717 --authenticationDatabase  admin -u root -p xxx dump(文件路径)


## 相关参考 
- [导出数据](Export-Data.md)
