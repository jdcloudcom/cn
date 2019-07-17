# uploadCert


## 描述
上传证书

## 请求方式
POST

## 请求地址
https://cdn.jdcloud-api.com/v1/sslCert:upload


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**certName**|String|True| |证书名称|
|**keyFile**|String|True| |私钥|
|**certFile**|String|True| |证书|
|**aliasName**|String|False| |证书别名|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|请求的标识Id|

### Result
|名称|类型|描述|
|---|---|---|
|**certId**|String| |
|**digest**|String|对私钥文件使用sha256算法计算的摘要信息|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
