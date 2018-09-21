# describeQuotas


## 描述
查询(k8s 集群)配额

## 请求方式
GET

## 请求地址
https://openapi.jke.jdcloud.com/v1/regions/{regionId}/quotas

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**filters**|Filter[]|False||resourceTypes - 资源类型，暂时只支持[kubernetes]<br>|

### Filter
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True||过滤条件的名称|
|**operator**|String|False||过滤条件的操作符，默认eq|
|**values**|String[]|True||过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|Result||


### Result
|名称|类型|描述|
|---|---|---|
|**quotas**|Quota[]|配额列表|
### Quota
|名称|类型|描述|
|---|---|---|
|**limit**|Integer|可用资源上限|
|**resourceType**|String|资源类型[kubernetes]|
|**used**|Integer|已用资源数量|

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**500**|Internal server error|
|**503**|Service unavailable|
|**200**|OK|
|**404**|Not found|
|**429**|Quota exceeded|
