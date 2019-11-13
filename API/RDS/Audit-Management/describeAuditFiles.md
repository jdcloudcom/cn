# describeAuditFiles


## 描述
获取当前实例下的所有审计结果文件的列表<br>- 仅支持SQL Server

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/audit:describeAuditFiles

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**auditFiles**|[AuditFile[]](#AuditFile)| |
### <a name="AuditFile">AuditFile</a>
|名称|类型|描述|
|---|---|---|
|**name**|String|审计日志文件名称|
|**sizeByte**|Long|审计日志文件大小，单位Byte|
|**lastUpdateTime**|String|审计日志文件最后更新时间|
|**uploadTime**|String|审计日志文件上传时间|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
