# queryUserDomains


## 描述
查询domian列表

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/userdomain

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False|1|页码|
|**pageSize**|Integer|False|20|分页大小，默认为20，取值范围：[10,100]|
|**orderBy**|String|False| |排序类型|
|**apiGroupId**|String|True| |api分组id|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](queryuserdomains#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**total**|Integer|total count|
|**data**|[DomainInfo[]](queryuserdomains#domaininfo)|key详情|
### <div id="domaininfo">DomainInfo</div>
|名称|类型|描述|
|---|---|---|
|**apiGroupId**|String|api分组id|
|**domainId**|String|域名id|
|**domain**|String|域名|
|**cname**|String|解析的cname|
|**protocol**|String|域名使用的协议|
|**createTime**|String|域名创建时间|
|**status**|String|域名状态|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
