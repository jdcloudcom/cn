# modifyWebRule


## 描述
更新某条网站类规则

## 请求方式
PATCH

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/webRules/{webRuleId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||实例ID|
|**regionId**|String|True||所属地域ID|
|**webRuleId**|String|True||网站规则ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**webRuleSpec**|[WebRuleSpec](##WebRuleSpec)|True||网站类规则参数|

### <a name="WebRuleSpec">WebRuleSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**algorithm**|String|False||转发规则：wrr->带权重的轮询 rr->不带权重的轮询|
|**customPortStatus**|Integer|False||是否为自定义端口号，0->默认 1->自定义|
|**domain**|String|False||子域名|
|**forceJump**|Integer|False||是否开启https强制跳转，当protocol为HTTP_HTTPS时可以配置该属性 0->不强跳 1->开启强跳|
|**httpOrigin**|Integer|False||是否开启http回源，0->不开启 1->开启，当勾选HTTPS时可以配置该属性|
|**httpsCertContent**|String|False||证书内容|
|**httpsPort**|String|False||HTTPS协议的端口号，如443,8443，多个端口号使用逗号分隔|
|**httpsRsaKey**|String|False||证书私钥|
|**onlineAddr**|String[]|False|||
|**originAddr**|[OriginAddrItem[]](##OriginAddrItem)|False|||
|**originDomain**|String|False||回源域名,originType为CNAME时需要指定该字段|
|**originType**|String|False||回源类型：A或者CNAME|
|**port**|String|False||HTTP协议的端口号，如80,81，多个端口号使用逗号分隔|
|**protocol**|String|False||协议：HTTP、HTTPS、HTTP_HTTPS|
### <a name="OriginAddrItem">OriginAddrItem</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**inJdCloud**|Boolean|False||是否为京东云内公网IP地址|
|**ip**|String|False||回源IP地址|
|**weight**|Integer|False||权重|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||



## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
|**404**|NOT_FOUND|
|**500**|INTERNAL_SERVER_ERROR|
