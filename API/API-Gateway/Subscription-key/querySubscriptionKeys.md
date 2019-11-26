# querySubscriptionKeys


## 描述
查询密钥列表

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/subscriptionKeys

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False|1|页码, 默认为1, 取值范围：[1,∞)|
|**pageSize**|Integer|False|20|分页大小，默认为20，取值范围：[10,100]|
|**filters**|[Filter[]](querysubscriptionkeys#filter)|False| |description - 名称，模糊匹配<br>subscriptionKeyId - subscriptionKeyId，精确匹配<br>orderBy - 排序类型 desc asc<br>|

### <div id="filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](querysubscriptionkeys#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**subscriptionKeys**|[SubscriptionKey[]](querysubscriptionkeys#subscriptionkey)|密钥详情|
|**totalCount**|Integer|查询的密钥数目|
### <div id="subscriptionkey">SubscriptionKey</div>
|名称|类型|描述|
|---|---|---|
|**subscriptionKeyId**|String|subscription Key id|
|**description**|String|描述|
|**subscriptionKey**|String|subscription Key|
|**name**|String|密钥名称|
|**createTime**|String|密钥创建时间|
|**bindGroups**|[BindGroups[]](querysubscriptionkeys#bindgroups)|绑定分组|
### <div id="bindgroups">BindGroups</div>
|名称|类型|描述|
|---|---|---|
|**deploymentId**|String|部署ID|
|**groupName**|String|分组名称|
|**environment**|String|环境：test、preview、online|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
