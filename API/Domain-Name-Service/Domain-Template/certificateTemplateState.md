# certificateTemplateState


## 描述
查询域名信息模板实名认证状态

## 请求方式
GET

## 请求地址
https://domain.jdcloud-api.com/v1/regions/{regionId}/template/{templateId}/certificate

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**templateId**|Long|True| |模板ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](certificateTemplateState#result)| |
|**requestId**|String|此次请求的ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**certificateState**|Integer|实名认证状态 0未实名认证 1已实名认证 2审核中 3审核失败 4实名资料上传注册局失败|
|**certificateUnpassReason**|String|实名认证失败原因|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
