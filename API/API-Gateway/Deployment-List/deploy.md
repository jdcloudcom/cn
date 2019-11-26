# deploy


## 描述
发布版本

## 请求方式
POST

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/apiGroups/{apiGroupId}/deployments

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**apiGroupId**|String|True| |分组ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**revision**|String|True| |发布的修订版本号|
|**environment**|String|True| |环境：test、preview、online|
|**backendServiceType**|String|False| |后端服务类型：mock、unique、vpc|
|**backendUrl**|String|False| |后端地址|
|**description**|String|False| |描述|
|**jdsfName**|String|False| |微服务网关名称|
|**jdsfRegistryName**|String|False| |微服务注册中心ID|
|**jdsfId**|String|False| |微服务ID|


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
