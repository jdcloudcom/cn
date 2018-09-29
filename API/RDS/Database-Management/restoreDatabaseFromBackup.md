# restoreDatabaseFromBackup


## 描述
从备份中恢复单个数据库，支持从其他实例（但必须是同一个账号下的实例）备份中恢复。例如可以从生产环境的数据库实例的备份恢复到测试环境的数据库中。<br>- 仅支持SQL Server

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/databases/{dbName}:restoreDatabaseFromBackup

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dbName**|String|True| |库名称|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**backupFileName**|String|True| |指定该备份中用于恢复数据库的文件名称。通常情况下文件名（不包括后缀）即为备份的数据库名。例如文件名为my_test_db.bak，表示该文件是my_test_db数据库的备份|
|**backupId**|String|True| |备份ID，可从备份查询接口describeBackups获取|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
