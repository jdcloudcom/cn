# createTemplate


## 描述
创建域名信息模板

## 请求方式
POST

## 请求地址
https://domain.jdcloud-api.com/v1/regions/{regionId}/template

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**userNameCh**|String|True| |联系人姓名(中文),必填,必须含有中文,只允许输入特殊字符(.,、·()()-""“”/\'),最多可输入64 字符|
|**userNameEn1**|String|True| |联系人姓(英文),必填,必须含有英文,只允许输入特殊字符(.,、·()()-""“”/\'),最多可输入64 字符|
|**userNameEn2**|String|True| |联系人名(英文),必填,必须含有英文,只允许输入特殊字符(.,、·()()-""“”/\'),最多可输入64 字符|
|**ownerNameCh**|String|True| |域名所有者或所有者单位名称(中文),必填,必须含有中文,只允许输入特殊字符(.,、·()()-""“”/\'),最多可输入64 字符|
|**ownerNameEn**|String|True| |域名所有者或所有者单位名称(英文),必填,必须含有中文,只允许输入特殊字符(.,、·()()-""“”/\'),最多可输入64 字符|
|**nationCodeCh**|String|True| |国家及地区（中文）|
|**nationCodeEn**|String|True| |国家及地区（英文）|
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
|**result**|[Result](createTemplate#result)| |
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
