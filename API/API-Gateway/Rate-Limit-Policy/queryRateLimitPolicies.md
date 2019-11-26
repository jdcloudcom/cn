# queryRateLimitPolicies


## 描述
查询流控策略列表

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/rateLimitPolicies

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False|1|页码, 默认为1, 取值范围：[1,∞)|
|**pageSize**|Integer|False|20|分页大小，默认为20，取值范围：[10,100]|
|**filters**|[Filter[]](queryratelimitpolicies#filter)|False| |policyName - 策略名称，模糊匹配<br>|

### <div id="filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](queryratelimitpolicies#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**rateLimitPolicys**|[RateLimitPolicy[]](queryratelimitpolicies#ratelimitpolicy)|查询的所有流控策略详情|
|**totalCount**|Integer|查询的流控策略数目|
### <div id="ratelimitpolicy">RateLimitPolicy</div>
|名称|类型|描述|
|---|---|---|
|**policyId**|String|策略id|
|**policyName**|String|策略名称|
|**timeUnit**|String|时间单位|
|**apiLimitCount**|Integer|api流量限制次数|
|**userLimitCount**|Integer|用户流量限制次数|
|**appLimitCount**|Integer|应用流量限制次数|
|**userId**|String|用户ID|
|**pin**|String|用户名|
|**description**|String|描述|
|**bindGroups**|String|绑定分组，以逗号隔开的分组id存储，以逗号隔开的分组name返回|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
