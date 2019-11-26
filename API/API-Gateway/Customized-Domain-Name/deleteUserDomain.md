# deleteUserDomain


## 描述
删除用户域名接口

## 请求方式
DELETE

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/userdomain

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainIds**|String|True| |要删除domain的id集合，以,分隔|
|**apiGroupId**|String|False| |api分组id|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
