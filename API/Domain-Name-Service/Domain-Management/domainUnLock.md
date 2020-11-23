# domainUnLock


## 描述
域名解锁，取消域名禁止转移的状态

## 请求方式
POST

## 请求地址
https://domain.jdcloud-api.com/v1/regions/{regionId}/domain:unlock

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
|**requestId**|String|此次请求的ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
