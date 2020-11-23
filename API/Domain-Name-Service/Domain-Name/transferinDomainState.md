# transferinDomainState


## 描述
域名转入状态查询

## 请求方式
GET

## 请求地址
https://domain.jdcloud-api.com/v1/regions/{regionId}/transferin

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|True| |要转入的域名|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](transferinDomainState#result)| |
|**requestId**|String|此次请求的ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**transferInState**|Integer|转入状态：0转入失败 1验证邮箱 2转入处理中 3转入成功|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
