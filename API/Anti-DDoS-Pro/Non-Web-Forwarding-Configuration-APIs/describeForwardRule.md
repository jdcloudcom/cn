# describeForwardRule


## 描述
查询非网站类规则

## 请求方式
GET

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/forwardRules/{forwardRuleId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**forwardRuleId**|String|True| |转发规则 ID|
|**instanceId**|String|True| |实例 ID|
|**regionId**|String|True| |Region ID|

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
|**data**|ForwardRule| |
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
