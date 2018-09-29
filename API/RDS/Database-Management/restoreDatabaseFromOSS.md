# restoreDatabaseFromOSS


## 描述
从上传到OSS的备份文件中恢复单个数据库<br>- 仅支持SQL Server

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/databases/{dbName}:restoreDatabaseFromOSS

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dbName**|String|True| |库名称|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ossURL**|String|True| |用户上传到对象存储OSS上的备份文件的内链|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
