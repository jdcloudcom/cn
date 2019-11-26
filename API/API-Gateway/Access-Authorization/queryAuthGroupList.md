# queryAuthGroupList


## 描述
查询可绑定部署列表

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/accessAuths:groupList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**authUserType**|String|True| |待绑定的用户类型|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](queryauthgrouplist#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**bindGroups**|[BindGroups[]](queryauthgrouplist#bindgroups)|查询可绑定的部署列表|
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
