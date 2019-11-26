# queryKeyInfo


## 描述
查询key详情

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/kms/{keyId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**keyId**|String|True| |keyId|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](querykeyinfo#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**keyInfo**|[KeyInfo](querykeyinfo#keyinfo)| |
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
