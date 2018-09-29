# modifyCacheInstanceAttribute


## 描述
修改缓存Redis实例的资源名称、描述，二者至少选一

## 请求方式
PATCH

## 请求地址
https://redis.jdcloud-api.com/v1/regions/{regionId}/cacheInstance/{cacheInstanceId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cacheInstanceId**|String|True| |缓存Redis实例ID，是访问实例的唯一标识。|
|**regionId**|String|True| |缓存Redis实例所在区域的Region ID。目前缓存Redis有华北、华南、华东区域，对应Region ID为cn-north-1、cn-south-1、cn-east-2|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cacheInstanceDescription**|String|False| |缓存Redis实例资源描述，不能超过256个字符|
|**cacheInstanceName**|String|False| |缓存Redis实例资源名称，名称只支持数字、字母、英文下划线、中文，且不少于2字符不超过32字符|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|本次修改请求的ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
