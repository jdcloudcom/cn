# queryBindGroupKey


## 描述
查询绑定分组详情

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/accessKeys/{accessKeyId}:bindGroup

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**accessKeyId**|String|True| |access key id|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](querybindgroupkey#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**bindGroups**|[BindGroups[]](querybindgroupkey#bindgroups)|绑定部署ID和名称|
### <div id="bindgroups">BindGroups</div>
|名称|类型|描述|
|---|---|---|
|**deploymentId**|String|部署ID|
|**groupName**|String|分组名称|
|**environment**|String|环境：test、preview、online|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
