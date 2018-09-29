# createAudit


## 描述
开启SQL Server的数据库审计功能，目前支持实例级的数据库审计。用户可以根据需要开启、关闭审计、自定义审计策略，并下载审计文件。审计文件为原生的SQL Server审计文件，缺省保存6个月。<br>- 仅支持SQL Server

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/audit

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**enabled**|String|True| |要开启的审计选项，各个选项之间用英文逗号或空格进行分割，例如：DATABASE_OBJECT_ACCESS_GROUP,ACKUP_RESTORE_GROU等<br>各个数据库版本支持的审计选项可以通过接口[getAuditOptions](./getAuditOptions.md)获得，各个审计项的具体含义可以参看微软的官方文档|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
