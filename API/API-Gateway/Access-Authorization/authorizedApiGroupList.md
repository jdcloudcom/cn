# authorizedApiGroupList


## 描述
查询所有已授权api分组列表

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/accessAuths:authorizedApiGroupList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False|1|页码, 默认为1, 取值范围：[1,∞)|
|**pageSize**|Integer|False|20|分页大小，默认为20，取值范围：[10,100]|
|**filters**|[Filter[]](authorizedapigrouplist#filter)|False| |apiGroupName - 名称，模糊匹配<br>|

### <div id="filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](authorizedapigrouplist#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**apiGroups**|[UserBindedGroups[]](authorizedapigrouplist#userbindedgroups)|查询的API分组信息|
### <div id="userbindedgroups">UserBindedGroups</div>
|名称|类型|描述|
|---|---|---|
|**apiGroupId**|String|分组ID|
|**groupName**|String|分组名称|
|**region**|String|区域|
|**authtime**|String|授权时间|
|**authUserType**|String|授权用户类型|
|**accessKey**|String|Access Key|
|**appId**|String|api调用者的appid|
|**environment**|String|api部署的环境|
|**revision**|String|api版本|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
