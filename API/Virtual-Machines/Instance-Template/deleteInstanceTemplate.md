# deleteInstanceTemplate


## 描述
删除一个启动模板


## 请求方式
DELETE

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/instanceTemplates/{instanceTemplateId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**instanceTemplateId**|String|True| |启动模板ID|

## 请求参数
无


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
