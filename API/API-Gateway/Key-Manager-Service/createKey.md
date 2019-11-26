# createKey


## 描述
创建key

## 请求方式
POST

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/kms

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**keyName**|String|False| |key 名称|
|**keyDesc**|String|False| |key 描述|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createkey#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**accessKey**|String|生成的accessKey|
|**secretKey**|String|生成的secretKey|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
