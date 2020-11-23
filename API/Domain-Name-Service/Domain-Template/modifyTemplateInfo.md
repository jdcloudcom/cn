# modifyTemplateInfo


## 描述
修改域名信息模板

## 请求方式
PUT

## 请求地址
https://domain.jdcloud-api.com/v1/regions/{regionId}/template/{templateId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**templateId**|Long|True| |模板ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**nationCodeCh**|String|True| |国家及地区（中文）|
|**nationCodeEn**|String|True| |国家及地区（英文）中国：china|
|**provinceCodeCh**|String|True| |省份（中文）|
|**provinceCodeEn**|String|True| |省份（英文）|
|**cityCodeCh**|String|True| |城市（中文）|
|**cityCodeEn**|String|True| |城市（英文）|
|**addressCh**|String|True| |通信地址（中文）|
|**addressEn**|String|True| |通信地址（英文）|
|**zipCode**|String|True| |邮编 6位数字|
|**phone**|String|True| |联系电话，国家区号-地区区号(或手机号码前3位)-电话号码（或手机号码后8位) 例:86-138-12345678|
|**fax**|String|True| |传真，国家区号-地区区号(或手机号码前3位)-电话号码（或手机号码后8位) 例:86-138-12345678|
|**email**|String|True| |邮件|
|**ownerType**|Integer|True| |所有者类型  1个人 2企业|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](modifyTemplateInfo#result)| |
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
