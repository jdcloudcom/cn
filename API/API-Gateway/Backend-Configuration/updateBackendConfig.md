# updateBackendConfig


## 描述
修改后端配置

## 请求方式
PATCH

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/apiGroups/{apiGroupId}/backendConfig/{backendConfigId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**apiGroupId**|String|True| |分组ID|
|**backendConfigId**|String|True| |backendConfigId|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**baseGroupId**|String|False| |分组ID|
|**environment**|String|True| |环境：test、preview、online|
|**backendUrl**|String|False| |后端地址|
|**backendServiceType**|String|True| |后端服务类型：mock、HTTP/HTTPS|
|**headerParams**|[SimpleParameter[]](updatebackendconfig#simpleparameter)|False| |header参数列表|
|**queryParams**|[SimpleParameter[]](updatebackendconfig#simpleparameter)|False| |query参数列表|
|**description**|String|False| |描述|
|**createTime**|Long|False| |发布日期，格式为毫秒级时间戳|
|**sort**|Integer|True| |排序，赋值0时为默认的后端配置|
|**userSort**|Integer|False| |排序，用于展示使用|
|**jdsfId**|String|False| |vpc网关id|
|**jdsfParam**|String|False| |vpc后端地址|
|**jdsfRegion**|String|False| |vpc网关所属region|
|**jdsfPin**|String|False| |vpc网关创建者的pin|

### <div id="simpleparameter">SimpleParameter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |名称|
|**value**|String|False| |值|

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
