# resetCacheInstancePassword


## 描述
重置缓存Redis实例密码，支持免密操作

## 请求方式
POST

## 请求地址
https://redis.jdcloud-api.com/v1/regions/{regionId}/cacheInstance/{cacheInstanceId}:resetCacheInstancePassword

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cacheInstanceId**|String|True| |缓存Redis实例ID，是访问实例的唯一标识。|
|**regionId**|String|True| |缓存Redis实例所在区域的Region ID。目前缓存Redis有华北、华南、华东区域，对应Region ID为cn-north-1、cn-south-1、cn-east-2|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**password**|String|False| |密码，为空即为免密，包含且只支持字母及数字，不少于8字符不超过16字符|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|本次重置请求的ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
