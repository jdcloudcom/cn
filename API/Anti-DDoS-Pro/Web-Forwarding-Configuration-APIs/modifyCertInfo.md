# modifyCertInfo


## 描述
编辑证书

## 请求方式
POST

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/webRules/{webRuleId}:modifyCertInfo

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |实例 ID|
|**regionId**|String|True| |Region ID|
|**webRuleId**|String|True| |网站规则 ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**certInfoModifySpec**|CertInfoModifySpec|True| |编辑证书请求参数|

### CertInfoModifySpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**httpsCertContent**|String|False| |证书内容|
|**httpsRsaKey**|String|False| |私钥|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
