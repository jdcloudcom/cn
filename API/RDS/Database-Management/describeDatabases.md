# describeDatabases


## 描述
获取当前实例的所有数据库详细信息的列表

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/databases

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dbName**|String|False| |数据库名。如果不指定数据库名，则返回所有数据库列表<br>- **MySQL：不支持该字段**<br>- **SQL Server：支持该字段**|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**databases**|Database[]| |
### Database
|名称|类型|描述|
|---|---|---|
|**accessPrivilege**|DBAccessPrivilege[]|该数据库相关账户权限列表|
|**characterSetName**|String|字符集，参见[枚举参数定义](../Enum-Definitions/Enum-Definitions.md)|
|**dbName**|String|数据库名称，具体规则可参见帮助中心文档:[名称及密码限制](../../../documentation/Cloud-Database-and-Cache/RDS/Introduction/Restrictions/SQLServer-Restrictions.md)|
|**dbStatus**|String|数据库状态，参见[枚举参数定义](../Enum-Definitions/Enum-Definitions.md)<br>- **MySQL：不支持，不返回该字段**<br>- **SQL Server：返回该字段**|
### DBAccessPrivilege
|名称|类型|描述|
|---|---|---|
|**accountName**|String|账号名称|
|**privilege**|String|该账号对数据库具有的权限，权限的具体定义可以参见[枚举参数定义](../Enum-Definitions/Enum-Definitions.md)|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
