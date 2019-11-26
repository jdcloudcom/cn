# describeRevisions


## 描述
查询修订版本列表

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/apiGroups/{apiGroupId}/revision

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**apiGroupId**|String|True| |分组ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False|1|页码, 默认为1, 取值范围：[1,∞)|
|**pageSize**|Integer|False|20|分页大小，默认为20，取值范围：[10,100]|
|**filters**|[Filter[]](describerevisions#filter)|False| |revision - 修订版本号，精确匹配<br>environment - 发布环境，模糊匹配<br>revisionNote - 修订备注，精确匹配<br>|

### <div id="filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describerevisions#result)|查询结果集|
|**requestId**|String|请求ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**revisions**|[RevisionList[]](describerevisions#revisionlist)|查询修订版本详情列表|
|**totalCount**|Integer|查询的版本数目|
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
