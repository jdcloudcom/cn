# describeCCGraph


## 描述
CC 防护流量报表

## 请求方式
GET

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/charts:CCGraph

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**endTime**|String|True| |查询的结束时间, UTC 时间, 格式：yyyy-MM-dd'T'HH:mm:ssZ|
|**instanceId**|String[]|False| |高防实例 ID, 可以传 0 个或多个|
|**startTime**|String|True| |开始时间, 最多查最近 60 天, UTC 时间, 格式：yyyy-MM-dd'T'HH:mm:ssZ|
|**subDomain**|String[]|False| |规则域名, 可以传 0 个或多个|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**postProtect**|Integer[]| |
|**preProtect**|Integer[]| |
|**time**|Integer[]| |
|**unit**|String|流量单位|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
