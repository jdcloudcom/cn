# getDomainQueryCount


## 描述
查看域名的解析次数

## 请求方式
GET

## 请求地址
https://clouddnsservice.jdcloud-api.com/v1/regions/{regionId}/domain/{domainId}/queryCount

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainId**|String|True| |域名ID|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|True| |查询的域名|
|**end**|String|True| |终止时间, UTC时间例如2017-11-10T23:00:00Z|
|**start**|String|True| |起始时间, UTC时间例如2017-11-10T23:00:00Z|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|此次请求的ID|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**time**|Integer[]|时间序列|
|**traffic**|Integer[]|数据序列|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|NOT_FOUND|
