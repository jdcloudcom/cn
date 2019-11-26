# queryAccessAuths


## 描述
查询访问授权列表

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/accessAuths

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False|1|页码, 默认为1, 取值范围：[1,∞)|
|**pageSize**|Integer|False|20|分页大小，默认为20，取值范围：[10,100]|
|**filters**|[Filter[]](queryaccessauths#filter)|False| |auth_user_type - 授权类型，默认为 全部类型<br>auth_user_id - 用户标识，精确匹配，jd_cloud（京东云用户）, jd_apikms（api网关签名密钥）, jd_subscription_key（订阅密钥）,jd_cloud_pin（激活用户）<br>|

### <div id="filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](queryaccessauths#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**accessAuths**|[AccessAuth[]](queryaccessauths#accessauth)|访问授权详情|
|**totalCount**|Integer|查询的访问授权数目|
### <div id="accessauth">AccessAuth</div>
|名称|类型|描述|
|---|---|---|
|**accessAuthId**|String|访问授权ID|
|**authUserType**|String|授权用户类型|
|**accessKey**|String|Access Key|
|**description**|String|描述|
|**bindGroups**|String|绑定分组,用英文逗号分隔|
|**appId**|String|api调用者的appid|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
