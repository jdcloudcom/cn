# describeQuota


## 描述
查询资源的配额，支持：原生容器 和 secret.


## 请求方式
GET

## 请求地址
https://nc.jdcloud-api.com/v1/regions/{regionId}/quotas

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**resourceType**|String|True| |resourceType - 资源类型，支持多个[container, secret]<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**quota**|Quota| |
### Quota
|名称|类型|描述|
|---|---|---|
|**limit**|Integer|配额|
|**used**|Integer|已使用的数目|

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
