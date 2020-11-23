# checkDomain


## 描述
检查域名是否可以注册

## 请求方式
GET

## 请求地址
https://domain.jdcloud-api.com/v1/regions/{regionId}/domain:check

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
|**result**|[Result](checkDomain#result)| |
|**requestId**|String|此次请求的ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[CheckDomain](checkDomain#checkdomain)|检查域名的返回结果|
### <div id="CheckDomain">CheckDomain</div>
|名称|类型|描述|
|---|---|---|
|**domainName**|String|域名字符串|
|**avail**|Integer|可用状态：1为可用，0为不可用|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
