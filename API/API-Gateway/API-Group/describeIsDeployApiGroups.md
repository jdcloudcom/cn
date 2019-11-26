# describeIsDeployApiGroups


## 描述
查询分组

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/apiGroups:isDeploy

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**filters**|[Filter[]](describeisdeployapigroups#filter)|False| |deployStatus - 发布状态，已发布：1，未发布：0<br>|

### <div id="filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeisdeployapigroups#result)|查询结果集|
|**requestId**|String|请求ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**apiGroups**|[ApiGroup[]](describeisdeployapigroups#apigroup)|查询的API分组详情列表|
|**totalCount**|Integer|查询的分组数目|
### <div id="apigroup">ApiGroup</div>
|名称|类型|描述|
|---|---|---|
|**apiGroupId**|String|分组ID|
|**groupName**|String|名称|
|**description**|String|描述|
|**prefix**|String|分组路径前缀|
|**version**|String|版本号|
|**regionId**|String|区域|
|**domain**|String|域名|
|**environment**|String|发布环境信息，若为空或null，则未发布|
|**keyCheck**|String|密钥验证方式：check_exist（密钥必须在访问授权中已配置）、no_check_exist（无需事先配置）|
|**authType**|String|访问授权方式：None（免鉴权）、jd_cloud（开启访问授权，且必须使用京东云的AK、SK验签）、hufu（虎符用户）|
|**prefixStrip**|Integer|是否转发分组路径到后端服务：0（不转发）、1（转发）|
|**groupType**|String|分组类型：api_group（api分组）、jdsf_group（微服务分组）|
|**jdsfName**|String|微服务网关名称|
|**jdsfRegistryName**|String|微服务注册中心ID|
|**jdsfId**|String|微服务网关ID|
|**deploy**|Integer|分组是否已发布：0（未发布）、1（发布）|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**500**|Internal server error|
|**503**|Service unavailable|
