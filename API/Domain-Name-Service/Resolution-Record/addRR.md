# addRR


## 描述
添加域名的解析记录

## 请求方式
POST

## 请求地址
https://clouddnsservice.jdcloud-api.com/v1/regions/{regionId}/domain/{domainId}/RRAdd

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainId**|String|True| |域名ID|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|AddRR|True| |RR参数|

### AddRR
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**hostRecord**|String|False| |主机记录|
|**hostValue**|String|False| |解析记录的值|
|**jcloudRes**|Boolean|False| |是否是京东云资源|
|**mxPriority**|Integer|False| |优先级，只存在于某些解析记录类型|
|**port**|Integer|False| |端口，只存在于某些解析记录类型|
|**ttl**|Integer|False| |解析记录的生存时间|
|**type**|String|False| |解析的类型|
|**viewValue**|Integer|False| |解析线路的ID|
|**weight**|Integer|False| |解析记录的权重|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|此次请求的ID|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**dataList**|RR|添加成功后的解析记录结果|
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
