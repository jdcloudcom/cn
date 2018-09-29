# createNetworkAcl


## 描述
创建networkAcl接口

## 请求方式
POST

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/networkAcls/

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**description**|String|False| |描述,允许输入UTF-8编码下的全部字符，不超过256字符|
|**networkAclName**|String|True| |networkAcl名称|
|**vpcId**|String|True| |私有网络id|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|
|**result**|Result|返回结果|

### Result
|名称|类型|描述|
|---|---|---|
|**networkAclId**|String|networkAcl ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|Successful operation|
|**400**|Invalid parameter|
|**404**|Not found|
|**500**|Internal error|
|**429**|Quota exceeded|
