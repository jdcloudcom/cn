# searchRR


## 描述
查询主域名的解析记录

## 请求方式
GET

## 请求地址
https://clouddnsservice.jdcloud-api.com/v1/regions/{regionId}/domain/{domainId}/RR

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainId**|String|True| |域名ID|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |当前页数，起始值为1，默认为1|
|**pageSize**|Integer|False| |分页查询时设置的每页行数, 默认为10|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|此次请求的ID|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**currentCount**|Integer|当前页解析记录的个数|
|**dataList**|RR[]|解析记录列表|
|**totalCount**|Integer|所有解析记录的个数|
|**totalPage**|Integer|所有解析记录的页数|
### RR
|名称|类型|描述|
|---|---|---|
|**hostRecord**|String|主机记录|
|**hostValue**|String|解析记录的值|
|**id**|Integer|域名解析的唯一ID|
|**jcloudRes**|Boolean|是否是京东云资源|
|**mxPriority**|Integer|优先级，只存在于某些解析记录类型|
|**port**|Integer|端口，只存在于某些解析记录类型|
|**ttl**|Integer|解析记录的生存时间|
|**type**|String|解析记录的类型|
|**viewValue**|Integer[]|解析线路的ID|
|**weight**|Integer|解析记录的权重|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
