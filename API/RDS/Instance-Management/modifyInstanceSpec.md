# modifyInstanceSpec


## 描述
实例扩容，支持升级实例的CPU，内存及磁盘。

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:modifyInstanceSpec

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**newInstanceClass**|String|True| |扩容后实例规格|
|**newInstanceStorageGB**|Integer|True| |扩容后实例磁盘大小|
|**newInstanceStorageType**|String|False| |存储类型，如果不指定，默认会采用实例原存储类型.|
|**storageEncrypted**|Boolean|False| |实例数据加密(存储类型为云硬盘才支持数据加密). false：不加密; true：加密. 如果实例从本地盘变为云硬盘，缺省为false. 如果实例本来就是使用云硬盘的，缺省和源实例保持一致|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**orderId**|String|生成的订单号|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
