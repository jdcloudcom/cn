# createDatabase


## 描述
创建一个数据库。 为了实例的管理和数据恢复，RDS对用户权限进行了限制，用户仅能通过控制台或本接口创建数据库

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/databases

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**characterSetName**|String|True| |数据库的字符集名，当前支持的字符集请查看[枚举参数定义](../Enum-Definitions/Enum-Definitions.md)|
|**dbName**|String|True| |数据库名，数据库名称的限制请参考[帮助中心文档](../../../documentation/Cloud-Database-and-Cache/RDS/Introduction/Restrictions/SQLServer-Restrictions.md)|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
