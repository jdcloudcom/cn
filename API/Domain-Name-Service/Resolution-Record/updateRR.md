# updateRR


## 描述
修改主域名的某个解析记录

## 请求方式
POST

## 请求地址
https://clouddnsservice.jdcloud-api.com/v1/regions/{regionId}/domain/{domainId}/RRUpdate

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainId**|String|True| |域名ID|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|UpdateRR|True| |updateRR参数|

### UpdateRR
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|False| |主域名|
|**hostRecord**|String|False| |主机记录|
|**hostValue**|String|False| |解析记录的值|
|**id**|Integer|False| |域名解析的唯一ID|
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


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
