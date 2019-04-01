# checkDomainIcp


## 描述
校验域名是否备案

## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/domains:check


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domain**|String|True| |域名|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|ruquestId|

### Result
|名称|类型|描述|
|---|---|---|
|**icpStatus**|Boolean|备案状态|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
