# describeForwardRules


## 描述
查询某个实例下的非网站转发配置

## 请求方式
GET

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/forwardRules

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |实例 ID|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |页码, 默认为1|
|**pageSize**|Integer|False| |分页大小, 默认为10, 取值范围[10, 100]|
|**searchType**|String|False| |查询类型名称, domain:源站域名, ip:源站 IP, port: 转发端口, originPort: 源站端口|
|**searchValue**|String|False| |查询类型值|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**dataList**|ForwardRule[]| |
|**totalCount**|Integer| |
### ForwardRule
|名称|类型|描述|
|---|---|---|
|**algorithm**|String|转发规则：wrr->带权重的轮询，wlc->加权最小连接，rr->不带权重的轮询，sh->源地址hash|
|**cname**|String|规则的cname|
|**id**|Integer|规则id|
|**instanceId**|Integer|实例id|
|**onlineAddr**|String[]| |
|**originAddr**|OriginAddrItem[]| |
|**originDomain**|String|回源域名|
|**originPort**|Integer|回源端口号|
|**originType**|String|回源类型：ip或者domain|
|**port**|Integer|端口号|
|**protocol**|String|TCP或UDP|
|**status**|Integer|0防御状态，1回源状态|
### OriginAddrItem
|名称|类型|描述|
|---|---|---|
|**inJdCloud**|Boolean|是否为京东云内公网ip|
|**ip**|String|回源ip|
|**weight**|Integer|权重|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
