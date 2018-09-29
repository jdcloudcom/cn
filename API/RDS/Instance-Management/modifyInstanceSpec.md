# modifyInstanceSpec


## 描述
实例扩容，支持升级实例的CPU，内存及磁盘。目前暂不支持实例降配<br>- 仅支持MySQL

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:modifyInstanceSpec

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**newInstanceClass**|String|True| |扩容后实例规格|
|**newInstanceStorageGB**|Integer|True| |扩容后实例磁盘大小|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**orderId**|String|生成的订单号|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
