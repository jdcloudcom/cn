# describeDeployments


## 描述
查询部署列表

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/apiGroups/{apiGroupId}/deployments

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**apiGroupId**|String|True| |分组ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**filters**|[Filter[]](describedeployments#filter)|False| |isApiProduct - 是否API产品，精确匹配，1为是<br>|

### <div id="filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describedeployments#result)|查询结果集|
|**requestId**|String|请求ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**deployments**|[Deployment[]](describedeployments#deployment)|部署列表|
### <div id="deployment">Deployment</div>
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
|**500**|Internal server error|
|**503**|Service unavailable|
