# domainInfo


## 描述
查询用户的域名信息

## 请求方式
GET

## 请求地址
https://domain.jdcloud-api.com/v1/regions/{regionId}/domain

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|True| |要注册的域名|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](domainInfo#result)| |
|**requestId**|String|此次请求的ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[DomainInfo](domainInfo#domaininfo)|域名信息返回结果|
### <div id="DomainInfo">DomainInfo</div>
|名称|类型|描述|
|---|---|---|
|**domainName**|String|域名|
|**domainState**|Integer|域名状态 0失败 1正常 2预注册 3过期 4转出中 5已转出 6过户中|
|**templateId**|Long|模板ID|
|**startDate**|String|域名起始时间|
|**endDate**|String|域名结束时间|
|**cloudDnsId**|String|京东云解析域名ID|
|**modified**|String|最后变更时间|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
