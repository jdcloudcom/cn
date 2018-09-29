# deleteKeypair


## 描述
删除ssh密钥对。


## 请求方式
DELETE

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/keypairs/{keyName}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**keyName**|String|True| |密钥名称|
|**regionId**|String|True| |地域ID|

## 请求参数
无


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
