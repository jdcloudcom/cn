# deleteCacheInstance


## 描述
删除按配置计费、或包年包月已到期的单个缓存Redis实例，包年包月未到期不可删除
只有处于运行<b>running</b>或者错误<b>error</b>状态的可以删除，其余状态不可以删除
白名单用户不能删除包年包月已到期的云主机


## 请求方式
DELETE

## 请求地址
https://redis.jdcloud-api.com/v1/regions/{regionId}/cacheInstance/{cacheInstanceId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cacheInstanceId**|String|True| |缓存Redis实例ID，是访问实例的唯一标识。|
|**regionId**|String|True| |缓存Redis实例所在区域的Region ID。目前缓存Redis有华北、华南、华东区域，对应Region ID为cn-north-1、cn-south-1、cn-east-2|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|本次删除请求的ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
