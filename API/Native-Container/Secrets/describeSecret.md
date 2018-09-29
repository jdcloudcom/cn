# describeSecret


## 描述
查询单个 secret 详情


## 请求方式
GET

## 请求地址
https://nc.jdcloud-api.com/v1/regions/{regionId}/secrets/{name}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |Secret Name|
|**regionId**|String|True| |Region ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**secret**|Secret| |
### Secret
|名称|类型|描述|
|---|---|---|
|**createdAt**|String|创建时间|
|**data**|DockerRegistryData|机密的数据|
|**name**|String|机密数据名称|
|**type**|String|私密数据的类型，目前仅支持如下类型：docker-registry：用来和docker registry认证的类型|
### DockerRegistryData
|名称|类型|描述|
|---|---|---|
|**email**|String|邮件地址|
|**password**|String|密码|
|**server**|String|registry服务器地址|
|**username**|String|用户名|

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
