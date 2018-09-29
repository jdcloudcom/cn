# getAuditFiles


## 描述
获取当前实例下的所有审计结果文件的列表<br>- 仅支持SQL Server

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/audit:getAuditFiles

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**auditFiles**|AuditFile[]| |
### AuditFile
|名称|类型|描述|
|---|---|---|
|**lastUpdateTime**|String|审计日志文件最后更新时间|
|**name**|String|审计日志文件名称|
|**sizeByte**|Integer|审计日志文件大小，单位Byte|
|**uploadTime**|String|审计日志文件上传时间|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
