# createSecret


## 描述
创建一个 secret，用于存放镜像仓库机密相关信息。


## 请求方式
POST

## 请求地址
https://nc.jdcloud-api.com/v1/regions/{regionId}/secrets

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**data**|DockerRegistryData|False| |机密的数据。<br><br>key 的有效字符包括字母、数字、-、_和.； <br><br>value 是 Base64 编码的字符串，不能包含换行符（在 linux 下使用 base64 -w 0选项），每个value长度上限为4KB，整个data的长度不能超过256KB; <br><br>必须包含server、username、password 字段，email 字段是可选的。<br><br>|
|**name**|String|True| |机密数据名称，不能重复<br>|
|**secretType**|String|True| |机密数据的类型，目前仅支持：docker-registry 类型，用来和docker registry认证的类型。<br>|

### DockerRegistryData
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**email**|String|False| |邮件地址|
|**password**|String|True| |密码|
|**server**|String|True| |registry服务器地址|
|**username**|String|True| |用户名|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**secretName**|String| |

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**500**|Internal server error|
|**503**|Service unavailable|
|**200**|OK|
|**404**|Not found|
|**429**|Quota exceeded|
