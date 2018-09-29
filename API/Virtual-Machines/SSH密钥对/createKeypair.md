# createKeypair


## 描述
创建ssh密钥对。公钥部分存储在京东云，并返回未加密的 PEM 编码的 PKCS#8 格式私钥，您只有一次机会保存您的私钥。请妥善保管。<br>
若传入已存在的密钥名称，会返回错误。


## 请求方式
POST

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/keypairs

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**keyName**|String|True| |密钥对名称，需要全局唯一。只允许数字、大小写字母、下划线“_”及中划线“-”，不超过32个字符。<br>|


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
|**privateKey**|String|密钥对的私钥部分，PEM PKCS#8 格式。|

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
