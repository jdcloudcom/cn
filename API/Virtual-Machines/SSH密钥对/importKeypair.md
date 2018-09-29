# importKeypair


## 描述
导入由其他工具生成的密钥对的公钥部分。<br>
若传入已存在的密钥名称，会返回错误。


## 请求方式
POST

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/keypairs:import

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**keyName**|String|True| |密钥对名称，需要全局唯一。只允许数字、大小写字母、下划线“_”及中划线“-”，不超过32个字符。<br>|
|**publicKey**|String|True| |密钥对的公钥部分|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**keyFingerprint**|String|密钥对的指纹，根据 RFC4716 定义的公钥指纹格式，采用 MD5 信息摘要算法。|
|**keyName**|String|密钥对名称|

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
