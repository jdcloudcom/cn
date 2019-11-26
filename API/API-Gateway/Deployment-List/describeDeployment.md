# describeDeployment


## 描述
查询该版本的部署详情

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/apiGroups/{apiGroupId}/deployments/{deploymentId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**apiGroupId**|String|True| |分组ID|
|**deploymentId**|String|True| |部署ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describedeployment#result)|查询API分组详情|
|**requestId**|String|请求ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**deploymentId**|String|部署ID|
|**revision**|String|发布的修订版本号|
|**path**|String|路径|
|**environment**|String|环境：test、preview、online|
|**backendServiceType**|String|后端服务类型：mock、unique、vpc|
|**backendUrl**|String|后端地址|
|**description**|String|描述|
|**createTime**|Long|发布日期，格式为毫秒级时间戳|
|**jdsfName**|String|微服务网关名称|
|**jdsfRegistryName**|String|微服务注册中心ID|
|**jdsfId**|String|微服务ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
