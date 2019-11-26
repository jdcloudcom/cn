# queryBindGroupAuth


## 描述
查询已绑定详情

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/accessAuths/{accessAuthId}:bindGroup

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**accessAuthId**|String|True| |访问授权ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](querybindgroupauth#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**bindGroups**|[BindGroups[]](querybindgroupauth#bindgroups)|绑定部署ID和名称|
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
