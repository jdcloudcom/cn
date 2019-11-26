# deleteSubscriptionKey


## 描述
删除密钥

## 请求方式
DELETE

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/subscriptionKeys/{subscriptionKeyId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**subscriptionKeyId**|String|True| |subscription key id|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](deletesubscriptionkey#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**subscriptionKeyId**|String|已删除密钥Id|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
