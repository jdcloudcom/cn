# updateKey


## 描述
修改key信息

## 请求方式
PATCH

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/kms

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**keyId**|String|True| |keyid|
|**keyName**|String|False| |key 名称|
|**keyDesc**|String|False| | |


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
