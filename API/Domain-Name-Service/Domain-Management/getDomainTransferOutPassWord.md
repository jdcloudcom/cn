# getDomainTransferOutPassWord


## 描述
获取转移密码，用于域名转移注册商转出获取域名转移密码

## 请求方式
GET

## 请求地址
https://domain.jdcloud-api.com/v1/regions/{regionId}/domain:transferOut

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|True| |要修改的域名|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](getDomainTransferOutPassWord#result)| |
|**requestId**|String|此次请求的ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**passWord**|String|获取的转移密码，如果转移密码为空，则表示邮件已发送至域名对应的模板中的邮箱中|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
