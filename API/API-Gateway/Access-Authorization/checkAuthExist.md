# checkAuthExist


## 描述
检查accessAuth是否重复

## 请求方式
POST

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/accessAuths:checkAccessKeyExist

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**accessKey**|String|True| | |
|**authUserType**|String|True| | |


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](checkauthexist#result)|检查AccessAuth是否重复|
|**requestId**|String|请求ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**accessAuthId**|String|返回accessAuthId|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication falied|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
