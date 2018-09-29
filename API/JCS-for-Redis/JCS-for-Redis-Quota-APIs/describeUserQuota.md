# describeUserQuota


## 描述
查询账户配额信息

## 请求方式
GET

## 请求地址
https://redis.jdcloud-api.com/v1/regions/{regionId}/quota

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |缓存Redis实例所在区域的Region ID。目前缓存Redis有华北、华南、华东区域，对应Region ID为cn-north-1、cn-south-1、cn-east-2|

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
|**quota**|Quota| |
### Quota
|名称|类型|描述|
|---|---|---|
|**max**|Integer|配额|
|**name**|String|配额项的名称|
|**used**|Integer|已使用的数目|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
