# createRateLimitPolicy


## 描述
创建流控策略

## 请求方式
POST

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/rateLimitPolicies

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**rateLimitPolicyView**|[RateLimitPolicyView](createratelimitpolicy#ratelimitpolicyview)|False| |流控策略详情|

### <div id="ratelimitpolicyview">RateLimitPolicyView</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**policyName**|String|False| |策略名称|
|**timeUnit**|String|False| |时间单位|
|**apiLimitCount**|Integer|False| |api流量限制次数|
|**userLimitCount**|Integer|False| |用户流量限制次数|
|**appLimitCount**|Integer|False| |应用流量限制次数|
|**description**|String|False| |描述|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createratelimitpolicy#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**policyId**|String|流控策略Id|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
