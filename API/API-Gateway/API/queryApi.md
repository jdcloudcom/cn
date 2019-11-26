# queryApi


## 描述
查询单个api

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/apiGroups/{apiGroupId}/revision/{revision}/apis/{apiId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**apiGroupId**|String|True| |分组ID|
|**revision**|String|True| |版本号|
|**apiId**|String|True| |接口ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**filters**|[Filter[]](queryapi#filter)|False| |isApiProduct - 是否API产品，精确匹配，1为是<br>|

### <div id="filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](queryapi#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**api**|[Api](queryapi#api)| |
### <div id="api">Api</div>
|名称|类型|描述|
|---|---|---|
|**apiId**|String|apiId|
|**apiGroupId**|String|分组ID|
|**apiName**|String|名称|
|**action**|String|动作|
|**path**|String|请求路径|
|**matchType**|String|匹配模式：1."absolute"(绝对匹配); 2."prefix"（前缀匹配）;|
|**backServiceType**|String|后端类型，为空或null时前端显示未设置|
|**description**|String|描述|
|**reqParams**|[Parameter[]](queryapi#parameter)|请求参数列表|
|**reqBody**|String|请求格式|
|**resBody**|String|返回格式|
|**reqBodyType**|Integer|请求格式类型,1:application/json,2:text/xml,3:其他|
|**resBodyType**|Integer|返回格式类型,1:application/json,2:text/xml,3:其他|
|**apiBackendConfig**|[ApiBackendConfig](queryapi#apibackendconfig)|api后端配置|
|**hufuAppTypeId**|Integer|应用类型ID,云鼎业务线专用|
|**deploymentEnvironment**|String[]|当前分组版本，发布的环境信息|
|**editableReqBodyType**|String|请求格式类型,当reqBodyType等于3时,使用该请求格式类型|
|**editableResBodyType**|String|响应格式类型,当resBodyType等于3时,使用该响应格式类型|
|**wafStatus**|String|waf状态，如：observe,deny,off|
### <div id="apibackendconfig">ApiBackendConfig</div>
|名称|类型|描述|
|---|---|---|
|**backendPath**|String|后端路径|
|**backendAction**|String|后端请求方式|
|**backendParams**|[BackendParameter[]](queryapi#backendparameter)|后端参数列表|
|**backendConstParams**|[Parameter[]](queryapi#parameter)|后端常量参数列表|
### <div id="parameter">Parameter</div>
|名称|类型|描述|
|---|---|---|
|**name**|String|名称|
|**description**|String|描述|
|**paramLocation**|String|参数位置|
|**paramType**|String|参数类型|
|**defaultValue**|String|默认值|
|**isRequired**|Boolean|默认值|
### <div id="backendparameter">BackendParameter</div>
|名称|类型|描述|
|---|---|---|
|**backendName**|String|后端参数名称|
|**backendParamLocation**|String|后端参数位置|
|**name**|String|入参名称|
|**paramLocation**|String|入参位置|
|**paramType**|String|入参类型|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
