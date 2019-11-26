# updateApi


## 描述
修改api

## 请求方式
PUT

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
|**api**|[CreateApi](updateapi#createapi)|False| |api|

### <div id="createapi">CreateApi</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**apiGroupId**|String|True| |分组ID|
|**apiName**|String|True| |名称|
|**action**|String|True| |动作|
|**path**|String|True| |请求路径|
|**matchType**|String|True| |匹配模式：1."absolute"(绝对匹配); 2."prefix"（前缀匹配）;|
|**description**|String|False| |描述|
|**reqParams**|[Parameter[]](updateapi#parameter)|False| |请求参数列表|
|**reqBody**|String|False| |请求格式|
|**resBody**|String|False| |返回格式|
|**reqBodyType**|Integer|True| |请求格式类型,1:application/json,2:text/xml,3:其他|
|**resBodyType**|Integer|False| |返回格式类型,1:application/json,2:text/xml,3:其他|
|**apiBackendConfig**|[ApiBackendConfig](updateapi#apibackendconfig)|False| |api后端配置|
|**backServiceType**|String|False| |后端服务类型，如HTTP/HTTPS,mock,funcion等|
|**backServicePath**|String|False| |后端服务地址，如后端服务地址，funtion路径等|
|**backServiceId**|String|False| |后端服务ID，如函数ID等|
|**backServiceName**|String|False| |后端服务名称，如函数名称|
|**backUrl**|String|False| |后端地址|
|**backServiceConfig**|Boolean|True| |后端服务配置，为true时，采用与分组统一的配置，初始创建api时请设置为True。|
|**backServiceVersion**|String|False| |后端服务版本，如函数版本名称|
|**hufuAppTypeId**|Integer|False| |应用类型ID,云鼎业务线专用|
|**editableReqBodyType**|String|False| |请求格式类型,当reqBodyType等于3时,使用该请求格式类型|
|**editableResBodyType**|String|False| |响应格式类型,当resBodyType等于3时,使用该响应格式类型|
### <div id="apibackendconfig">ApiBackendConfig</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**backendPath**|String|False| |后端路径|
|**backendAction**|String|False| |后端请求方式|
|**backendParams**|[BackendParameter[]](updateapi#backendparameter)|False| |后端参数列表|
|**backendConstParams**|[Parameter[]](updateapi#parameter)|False| |后端常量参数列表|
### <div id="parameter">Parameter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |名称|
|**description**|String|False| |描述|
|**paramLocation**|String|False| |参数位置|
|**paramType**|String|False| |参数类型|
|**defaultValue**|String|False| |默认值|
|**isRequired**|Boolean|False| |默认值|
### <div id="backendparameter">BackendParameter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**backendName**|String|False| |后端参数名称|
|**backendParamLocation**|String|False| |后端参数位置|
|**name**|String|False| |入参名称|
|**paramLocation**|String|False| |入参位置|
|**paramType**|String|False| |入参类型|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](updateapi#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**apiId**|String|apiId|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
