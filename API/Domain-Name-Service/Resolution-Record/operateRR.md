# operateRR


## 描述
启用、停用、删除主域名下的解析记录

## 请求方式
POST

## 请求地址
https://clouddnsservice.jdcloud-api.com/v1/regions/{regionId}/domain/{domainId}/RROperate

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainId**|String|True||域名ID|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**action**|String|True||操作类型，on/off/del，分别是启用、停用、删除解析记录|
|**ids**|Integer[]|True||需要操作的解析记录ID|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||



## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
