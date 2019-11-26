# describeBackendConfig


## 描述
查询backendConfig

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/apiGroups/{apiGroupId}/backendConfig/{backendConfigId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**apiGroupId**|String|True| |分组ID|
|**backendConfigId**|String|True| |backendConfigId|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describebackendconfig#result)| |
|**requestId**|String|请求ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**backendConfig**|[BackendConfig](describebackendconfig#backendconfig)| |
### <div id="backendconfig">BackendConfig</div>
|名称|类型|描述|
|---|---|---|
|**backendConfigId**|String|接口ID|
|**baseGroupId**|String|分组ID|
|**environment**|String|环境：test、preview、online|
|**backendUrl**|String|后端地址|
|**backendServiceType**|String|后端服务类型：mock、HTTP/HTTPS|
|**headerParams**|[SimpleParameter[]](describebackendconfig#simpleparameter)|header参数列表|
|**queryParams**|[SimpleParameter[]](describebackendconfig#simpleparameter)|query参数列表|
|**description**|String|描述|
|**createTime**|Long|发布日期，格式为毫秒级时间戳|
|**sort**|Integer|排序，赋值0时为默认的后端配置|
|**userSort**|Integer|排序，用于展示使用|
|**jdsfId**|String|vpc网关id|
|**jdsfParam**|String|vpc后端地址|
|**jdsfRegion**|String|vpc网关所属region|
|**jdsfPin**|String|vpc网关创建者的pin|
### <div id="simpleparameter">SimpleParameter</div>
|名称|类型|描述|
|---|---|---|
|**name**|String|名称|
|**value**|String|值|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
