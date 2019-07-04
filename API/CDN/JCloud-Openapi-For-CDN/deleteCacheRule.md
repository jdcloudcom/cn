# deleteCacheRule


## 描述
删除缓存规则

## 请求方式
DELETE

## 请求地址
https://cdn.jdcloud-api.com/v1/domain/{domain}/cacheRule

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domain**|String|True| |用户域名|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**configId**|Long|False| |缓存规则配置ID|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Object| |
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
