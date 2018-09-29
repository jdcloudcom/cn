# setImportFileShared


## 描述
设置或取消上传文件是否共享给同一账号下的其他实例。缺省情况下，文件仅在上传的实例上可见并可导入，其他实例不可见不可导入。如果需要该文件在其他实例上也可导入，可将此文件设置为共享<br>- 仅支持SQL Server

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/importFiles/{fileName}:setShared

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**fileName**|String|True| |单库上云文件名|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**shared**|String|True| |文件是否共享<br>true:共享<br>false:不共享|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
