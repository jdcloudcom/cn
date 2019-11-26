# createUserDomain


## 描述
添加用户域名

## 请求方式
POST

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/userdomain

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domain**|String|True| |域名|
|**protocol**|String|False| |协议|
|**apiGroupId**|String|True| |api分组id|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createuserdomain#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**domainId**|String|生成的domainId|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
