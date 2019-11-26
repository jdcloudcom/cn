# modifyApiGroupAttribute


## 描述
修改API分组信息

## 请求方式
PUT

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/apiGroups/{apiGroupId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**apiGroupId**|String|True| |分组ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**groupName**|String|False| |名称|
|**description**|String|False| |描述|
|**prefix**|String|False| |分组路径前缀|
|**keyCheck**|String|False| |密钥验证方式：check_exist（密钥必须在访问授权中已配置）、no_check_exist（无需事先配置）|
|**authType**|String|False| |访问授权方式：None（免鉴权）、jd_cloud（开启访问授权，且必须使用京东云的AK、SK验签）、hufu（虎符用户）|
|**prefixStrip**|Integer|False| |是否转发分组路径到后端服务：0（不转发）、1（转发）默认为1|
|**groupType**|String|False| |分组类型：api_group（api分组）、jdsf_group（微服务分组）默认为 api_group|
|**jdsfName**|String|False| |微服务网关名称|
|**jdsfRegistryName**|String|False| |微服务注册中心ID|
|**jdsfId**|String|False| |微服务网关ID|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
