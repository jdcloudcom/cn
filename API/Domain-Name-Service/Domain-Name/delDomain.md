# delDomain


## 描述
删除主域名

## 请求方式
DELETE

## 请求地址
https://clouddnsservice.jdcloud-api.com/v1/regions/{regionId}/domainDel

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainId**|Integer|True| |需要删除的域名ID|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|此次请求的ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
