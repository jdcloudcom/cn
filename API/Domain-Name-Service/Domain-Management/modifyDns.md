# modifyDns


## 描述
根据域名修改域名对应的 DNS 信息

## 请求方式
PUT

## 请求地址
https://domain.jdcloud-api.com/v1/regions/{regionId}/domain:dns

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|True| |要修改的域名|
|**dns**|String[]|True| |要修改的DNS,个数要求再2个-6个之间|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|此次请求的ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
