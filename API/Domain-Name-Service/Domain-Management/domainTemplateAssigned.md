# domainTemplateAssigned


## 描述
通过已实名的信息模板，完成域名的快速过户

## 请求方式
POST

## 请求地址
https://domain.jdcloud-api.com/v1/regions/{regionId}/domain:assigned

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|True| |要修改的域名|
|**templateId**|Long|True| |要过户的模板ID|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|此次请求的ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
