# resetKey


## 描述
重置key的acesskey和secretkey

## 请求方式
PUT

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/kms

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**keyId**|String|True| |keyId|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](resetkey#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**keyInfo**|[KeyInfo](resetkey#keyinfo)| |
### <div id="keyinfo">KeyInfo</div>
|名称|类型|描述|
|---|---|---|
|**userId**|String|userid|
|**keyId**|String|keyid|
|**keyName**|String|keyname|
|**accessKey**|String|ak|
|**secretKey**|String|sk|
|**keyDesc**|String|key描述信息|
|**createTime**|String|创建时间|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
