# modifyInstanceIpWhiteList


## 描述
设置实例ip白名单

## 请求方式
POST

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:setIpWhiteList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||实例id|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ipWhiteList**|String[]|True||ip白名单列表|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||



## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
