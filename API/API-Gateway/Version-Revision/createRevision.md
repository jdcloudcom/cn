# createRevision


## 描述
创建修订版本

## 请求方式
POST

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/apiGroups/{apiGroupId}/revision

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**apiGroupId**|String|True| |分组ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**revision**|String|False| |修订版本号，如果创建版本时传回修订版本，此为必填项|
|**baseRevision**|String|False| |基于此版本，如果创建版本时传回修订版本，此为必填项|
|**revisionNote**|String|False| |修订备注|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createrevision#result)| |
|**requestId**|String|请求ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**revision**|String|新建的修订版本号|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
