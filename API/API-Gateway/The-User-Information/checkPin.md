# checkPin


## 描述
校验pin是否存在

## 请求方式
POST

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/pins/{pin}:checkPin

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pin**|String|True| |京东云pin|
|**regionId**|String|True| |地域ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication falied|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
