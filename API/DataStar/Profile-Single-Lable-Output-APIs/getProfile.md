# getProfile


## 描述
根据deviceId查询对应用户的画像信息

## 请求方式
GET

## 请求地址
https://datastar.cn-south-1.jdcloud-api.com/v1/regions/{regionId}/profile/getProfile

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**id**|String|True| |deviceId，mobile等,多个id英文逗号分隔|
|**labelCode**|String|True| |画像标签编号,多个画像标签英文逗号分隔|
|**type**|String|True| |数据类型,只能查询一种类型，支持类型：mobile、idfa、imei、md5_idfa、md5_imei|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID，每次请求都不一样|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|String|Map<String, Map<String,String>>序列化后的字符串，需要再次转换并使用。Key为对应的deviceId，value为对应的画像标签内容,value内map的key为画像的标签code，value为画像对应的值|
|**message**|String|描述信息|
|**status**|Boolean|true为成功，false为失败|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
