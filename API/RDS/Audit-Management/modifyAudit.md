# modifyAudit


## 描述
修改当前的审计选项。当前已有审计选项可以通过describeAudit获得，支持的全部选项可以通过getAuditOptions获得。<br>- 仅支持SQL Server

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/audit:modifyAudit

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**add**|String|False| |在原有审计项基础上，增加新的审计项，多个审计项之间用英文逗号，分号或空格分隔，例如DATABASE_OBJECT_ACCESS_GROUP,ACKUP_RESTORE_GROUP|
|**drop**|String|False| |删除审计项，多个审计项之间用英文逗号，分号或空格分隔，例如DATABASE_OBJECT_ACCESS_GROUP,ACKUP_RESTORE_GROUP<br>如删除了所有审计项，则审计自动关闭|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
