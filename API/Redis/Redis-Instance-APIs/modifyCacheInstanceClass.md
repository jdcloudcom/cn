# modifyCacheInstanceClass


## 描述
变更缓存Redis实例配置

## 请求方式
POST

## 请求地址
https://redis.jdcloud-api.com/v1/regions/{regionId}/cacheInstance/{cacheInstanceId}:modifyCacheInstanceClass

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cacheInstanceId**|String|True||缓存Redis实例ID|
|**regionId**|String|True||缓存Redis实例所在区域的Region ID。目前缓存Redis有华北、华南、华东区域，对应Region ID为cn-north-1、cn-south-1、cn-east-2|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cacheInstanceClass**|String|True||变更后的缓存Redis<a href="https://www.jdcloud.com/help/detail/411/isCatalog/1">实例规格代码</a>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**orderNum**|String||

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
