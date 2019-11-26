# updateAccessKey


## 描述
更新密钥

## 请求方式
PATCH

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/accessKeys/{accessKeyId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**accessKeyId**|String|True| |access key id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**description**|String|False| |描述|
|**accessKeyType**|String|False| |密钥类型|
|**accessKey**|String|False| |Access Key|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](updateaccesskey#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**accessKeyId**|String|已更新密钥Id|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
