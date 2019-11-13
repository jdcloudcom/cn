# restoreDatabaseFromOSS


## 描述
从上传到OSS的备份文件中恢复单个数据库<br>- 仅支持SQL Server

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/databases/{dbName}:restoreDatabaseFromOSS

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**dbName**|String|True| |库名称|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ossURL**|String|True| |用户上传到对象存储OSS上的备份文件的路径。<br>例如用户备份上传的bucket为db_backup，文件为test_server/db1.bak，那么ossULR为db_backup/test_server/db1.bak。<br>**授权说明**：需要授予账户ID：785455908940，对这个bucket的读取权限，具体步骤可以查看[文档](https://docs.jdcloud.com/cn/object-storage-service/set-bucket-policy-2)。|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
