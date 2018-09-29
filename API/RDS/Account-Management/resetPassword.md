# resetPassword


## 描述
重置数据库账号密码。如果用户忘记账号的密码，可以使用该接口重置指定账号密码。密码重置后，以前的密码将无法使用，必须使用重置后的新密码登录或连接数据库实例。

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/accounts/{accountName}:resetPassword

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**accountName**|String|True| |账号名，在同一个实例中账号名不能重复|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**accountPassword**|String|True| |新密码，密码的具体规则可参见帮助中心文档:[名称及密码限制](../../../documentation/Cloud-Database-and-Cache/RDS/Introduction/Restrictions/SQLServer-Restrictions.md)|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
