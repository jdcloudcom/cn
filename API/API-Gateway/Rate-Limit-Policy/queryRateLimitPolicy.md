# queryRateLimitPolicy


## 描述
查询单个流控策略

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/rateLimitPolicies/{policyId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**policyId**|String|True| |限流策略ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](queryratelimitpolicy#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**rateLimitPolicy**|[RateLimitPolicy](queryratelimitpolicy#ratelimitpolicy)| |
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
