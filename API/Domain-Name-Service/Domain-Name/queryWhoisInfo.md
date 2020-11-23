# queryWhoisInfo


## 描述
查询域名的whois信息

## 请求方式
GET

## 请求地址
https://domain.jdcloud-api.com/v1/regions/{regionId}/domain:whoisInfo

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|True| |要检查的域名|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](queryWhoisInfo#result)| |
|**requestId**|String|此次请求的ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[DomainWhoisInfo](queryWhoisInfo#domainwhoisinfo)|域名Whois返回结果|
### <div id="DomainWhoisInfo">DomainWhoisInfo</div>
|名称|类型|描述|
|---|---|---|
|**domainName**|String|域名|
|**whoisInfo**|String|whois信息|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
