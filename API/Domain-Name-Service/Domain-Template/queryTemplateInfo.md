# queryTemplateInfo


## 描述
查询域名信息模板

## 请求方式
GET

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
|**result**|[Result](queryTemplateInfo#result)| |
|**requestId**|String|此次请求的ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[TemplateInfo](queryTemplateInfo#templateinfo)|模板信息返回结果|
### <div id="TemplateInfo">TemplateInfo</div>
|名称|类型|描述|
|---|---|---|
|**userNameCh**|String|联系人姓名(中文)|
|**userNameEn1**|String|联系人姓(英文)|
|**userNameEn2**|String|联系人名(英文)|
|**ownerNameCh**|String|域名所有者或所有者单位名称(中文)|
|**ownerNameEn**|String|域名所有者或所有者单位名称(英文)|
|**nationCodeCh**|String|国家及地区（中文）|
|**nationCodeEn**|String|国家及地区（英文）|
|**provinceCodeCh**|String|省份（中文）|
|**provinceCodeEn**|String|省份（英文）|
|**cityCodeCh**|String|城市（中文）|
|**cityCodeEn**|String|城市（英文）|
|**addressCh**|String|通信地址（中文）|
|**addressEn**|String|通信地址（英文）|
|**zipCode**|String|邮编 6位数字|
|**phone**|String|联系电话，国家区号-地区区号(或手机号码前3位)-电话号码（或手机号码后8位) 例:86-138-12345678|
|**fax**|String|传真，国家区号-地区区号(或手机号码前3位)-电话号码（或手机号码后8位) 例:86-138-12345678|
|**email**|String|邮件|
|**ownerType**|Integer|所有者类型  1个人 2企业|
|**certificateStatus**|Integer|实名认证状态 0未实名认证 1已实名认证 2审核中 3审核失败 4实名资料上传注册局失败|
|**certificateUnpassReason**|String|实名认证失败原因|
|**modified**|String|修改时间|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
