# describeWebRule


## 描述
查询某条网站类规则

## 请求方式
GET

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/webRules/{webRuleId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||实例ID|
|**regionId**|String|True||所属地域ID|
|**webRuleId**|String|True||网站规则ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**data**|[WebRule](##WebRule)||
### <a name="WebRule">WebRule</a>
|名称|类型|描述|
|---|---|---|
|**algorithm**|String|转发规则：wrr->带权重的轮询 rr->不带权重的轮询|
|**ccStatus**|Integer|0->CC关闭 1->CC开启|
|**cname**|String|规则的cname|
|**customPortStatus**|Integer|是否为自定义端口号，0->默认 1->自定义|
|**domain**|String|子域名|
|**forceJump**|Integer|是否开启https强制跳转，当protocol为HTTP_HTTPS时可以配置该属性 0->不强跳 1->开启强跳|
|**httpCertStatus**|Integer|证书状态：0->异常 1->正常|
|**httpOrigin**|Integer|是否开启http回源，0->不开启 1->开启，当勾选HTTPS时可以配置该属性|
|**httpsCertContent**|String|证书内容|
|**httpsPort**|String|HTTPS协议的端口号，如443,8443，多个端口号使用逗号分隔|
|**httpsRsaKey**|String|证书私钥|
|**id**|Integer|规则ID|
|**instanceId**|Integer|实例ID|
|**onlineAddr**|String[]||
|**originAddr**|[OriginAddrItem[]](##OriginAddrItem)||
|**originDomain**|String|回源域名,originType为CNAME时返回该字段|
|**originType**|String|回源类型：A或者CNAME|
|**port**|String|HTTP协议的端口号，如80,81，多个端口号使用逗号分隔|
|**protocol**|String|协议：HTTP、HTTPS、HTTP_HTTPS|
|**status**|Integer|0->防御状态 1->回源状态|
### <a name="OriginAddrItem">OriginAddrItem</a>
|名称|类型|描述|
|---|---|---|
|**inJdCloud**|Boolean|是否为京东云内公网IP地址|
|**ip**|String|回源IP地址|
|**weight**|Integer|权重|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
