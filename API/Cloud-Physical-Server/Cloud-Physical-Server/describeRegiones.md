# describeRegiones


## 描述
查询云物理服务器地域列表

## 请求方式
GET

## 请求地址
https://cps.jdcloud-api.com/v1/regions

无

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
|**regions**|Region[]| |
### Region
|名称|类型|描述|
|---|---|---|
|**azs**|Az[]|可用区列表|
|**region**|String|地域代码, 如 cn-east-1|
|**regionName**|String|地域名称，如 华东一区|
### Az
|名称|类型|描述|
|---|---|---|
|**az**|String|可用区代码，如 cn-east-1a|
|**azName**|String|可用区名称|
|**region**|String|地域代码，如 cn-east-1|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Bad request|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
