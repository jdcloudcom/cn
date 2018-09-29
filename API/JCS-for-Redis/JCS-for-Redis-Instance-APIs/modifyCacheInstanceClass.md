# modifyCacheInstanceClass


## 描述
变更缓存Redis实例配置，只能变更运行状态的实例配置，变更配置的规格不能与之前的相同
预付费用户，从集群版变配到主从版，新规格的内存大小要大于老规格的内存大小，从主从版到集群版，新规格的内存大小要不小于老规格的内存大小


## 请求方式
POST

## 请求地址
https://redis.jdcloud-api.com/v1/regions/{regionId}/cacheInstance/{cacheInstanceId}:modifyCacheInstanceClass

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cacheInstanceId**|String|True| |缓存Redis实例ID，是访问实例的唯一标识。|
|**regionId**|String|True| |缓存Redis实例所在区域的Region ID。目前缓存Redis有华北、华南、华东区域，对应Region ID为cn-north-1、cn-south-1、cn-east-2|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cacheInstanceClass**|String|True| |变更后的缓存Redis规格，详细参见：<a href="https://www.jdcloud.com/help/detail/411/isCatalog/1">实例规格代码</a>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|本次变更请求的ID|
|**result**|Result|本次请求的结果信息。|

### Result
|名称|类型|描述|
|---|---|---|
|**orderNum**|String|本次变更请求的订单编号。|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
