# deleteTemplate


## 描述
删除域名信息模板

## 请求方式
DELETE

## 请求地址
https://domain.jdcloud-api.com/v1/regions/{regionId}/template/{templateId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**templateId**|Long|True| |模板ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](deleteTemplate#result)| |
|**requestId**|String|此次请求的ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**templateId**|Long|模板Id|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
