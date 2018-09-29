# getPackageId


## 描述
根据设备ID查询人群包ID

## 请求方式
GET

## 请求地址
https://datastar.cn-south-1.jdcloud-api.com/v1/regions/{regionId}/dmp/getPackageId

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**deviceIds**|String|True| |MD5（deviceId），多个MD5（deviceId）用英文逗号进行分割，注：MD5结果小写|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID，每次请求都不一样|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|String|Map<String,String>序列化后的字符串，需要再次转换并使用。Key为deviceId，value为人群包Id|
|**message**|String|描述信息|
|**status**|Boolean|true为成功，false为失败|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
