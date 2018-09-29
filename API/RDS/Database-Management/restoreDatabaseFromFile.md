# restoreDatabaseFromFile


## 描述
从用户通过单库上云工具上传到云上的备份文件中恢复单个数据库<br>- 仅支持SQL Server

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/databases/{dbName}:restoreDatabaseFromFile

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dbName**|String|True| |库名称|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**fileName**|String|True| |用户上传的备份文件名称（包括文件后缀名），例如mydb1.bak|
|**sharedFileGid**|String|False| |共享文件的全局ID，可从上传文件查询接口[describeImportFiles](../import/describeImportFiles.md)获取；如果该文件不是共享文件，则不用输入该参数|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
