# checkGroupNameExist


## 描述
检查分组名称是否重复,返回重复的apiGroupId,如果没有返回空

## 请求方式
POST

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/apiGroups:checkGroupNameExist

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**groupName**|String|True| |分组名称|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](checkgroupnameexist#result)|查询API分组详情|
|**requestId**|String|请求ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**apiGroupId**|String|分组id|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
