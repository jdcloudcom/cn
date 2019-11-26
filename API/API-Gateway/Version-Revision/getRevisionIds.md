# getRevisionIds


## 描述
查询分组内全部修订版本号

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/apiGroups/{apiGroupId}/revisions

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**apiGroupId**|String|True| |分组ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](getrevisionids#result)|查询结果集|
|**requestId**|String|请求ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**revisions**|[RevisionList[]](getrevisionids#revisionlist)|查询修订版本详情列表|
### <div id="revisionlist">RevisionList</div>
|名称|类型|描述|
|---|---|---|
|**revisionId**|String|版本Id|
|**revision**|String|修订版本号|
|**baseRevision**|String|基于此版本|
|**environment**|String|发布环境|
|**createdAt**|String|修订日期|
|**revisionNote**|String|修订备注|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**500**|Internal server error|
|**503**|Service unavailable|
