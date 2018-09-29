# describeCertInfo


## 描述
查询证书预览信息

## 请求方式
POST

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/webRule:describeCertInfo

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |实例 ID|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**certInfoDescribeSpec**|CertInfoDescribeSpec|True| |查询证书预览请求参数|

### CertInfoDescribeSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domain**|String|False| |域名|
|**httpsCertContent**|String|False| |证书内容|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|CertInfo| |
### CertInfo
|名称|类型|描述|
|---|---|---|
|**domain**|String|通用名称|
|**from**|String|证书生效时间|
|**issuer**|String|颁发者|
|**sigAlgName**|String|加密算法|
|**to**|String|证书到期时间|
|**user**|String|证书组织|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
