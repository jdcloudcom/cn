# modifyWebRule


## 描述
更新网站类规则

## 请求方式
PATCH

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/webRules/{webRuleId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |实例 ID|
|**regionId**|String|True| |Region ID|
|**webRuleId**|String|True| |网站规则 ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**webRuleSpec**|WebRuleSpec|True| |更新网站类规则请求参数|

### WebRuleSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**algorithm**|String|False| |转发规则：wrr->带权重的轮询，rr->不带权重的轮询|
|**customPortStatus**|Integer|False| |是否为自定义端口号，0为默认 1为自定义|
|**domain**|String|False| |子域名|
|**forceJump**|Integer|False| |是否开启https强制跳转，当protocol为HTTP_HTTPS时可以配置该属性 0为不强跳 1为开启强跳|
|**httpOrigin**|Integer|False| |是否开启http回源，0为不开启 1为开启，当勾选HTTPS时可以配置该属性|
|**httpsCertContent**|String|False| |证书内容|
|**httpsPort**|String|False| |HTTPS协议的端口号，如443,8443，多个端口号使用逗号分隔|
|**httpsRsaKey**|String|False| |证书私钥|
|**onlineAddr**|String[]|False| | |
|**originAddr**|OriginAddrItem[]|False| | |
|**originDomain**|String|False| |回源域名,originType为CNAME时需要指定该字段|
|**originType**|String|False| |回源类型：A或者CNAME|
|**port**|String|False| |HTTP协议的端口号，如80,81，多个端口号使用逗号分隔|
|**protocol**|String|False| |协议：HTTP、HTTPS、HTTP_HTTPS|
|**websocketStatus**|Integer|False| |是否开启 WebSocket, 0 为不开启, 1 为开启|
### OriginAddrItem
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**inJdCloud**|Boolean|False| |是否为京东云内公网ip|
|**ip**|String|False| |回源ip|
|**weight**|Integer|False| |权重|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
|**404**|NOT_FOUND|
|**500**|INTERNAL_SERVER_ERROR|
