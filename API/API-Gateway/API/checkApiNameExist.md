# checkApiNameExist


## 描述
创建API时，检查API名称是否重复,返回重复的apiId,如果没有返回空

## 请求方式
POST

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/apiGroups/{apiGroupId}/revision/{revision}/apis:checkApiNameExist

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**apiGroupId**|String|True| |分组ID|
|**revision**|String|True| |版本号|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**apiName**|String|True| |API名称|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](checkapinameexist#result)|检查API名称是否重复|
|**requestId**|String|请求ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**apiId**|String|API名称|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
