# describeQuotas


## 描述
查询配额，支持：云主机、镜像、密钥、模板、镜像共享


## 请求方式
GET

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/quotas

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**filters**|Filter[]|False| |resourceTypes - 资源类型，支持多个[instance，keypair，image，instanceTemplate，imageShare]<br>|
|**imageId**|String|False| |私有镜像Id，查询镜像共享(imageShare)配额时，此参数必传|

### Filter
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**quotas**|Quota[]|配额列表|
### Quota
|名称|类型|描述|
|---|---|---|
|**limit**|Integer|配额上限|
|**resourceType**|String|资源类型[instance，keypair，image，instanceTemplate]|
|**used**|Integer|已用配额|

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
