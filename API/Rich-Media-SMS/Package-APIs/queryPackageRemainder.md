# queryPackageRemainder


## 描述
套餐包余量，仅预付费用户使用

## 请求方式
POST

## 请求地址
https://rms.jdcloud-api.com/v2/regions/{regionId}/queryPackageRemainder

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True|cn-north-1|Region ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|RespPackageResult|响应数据|
|**status**|Boolean|请求状态|
|**code**|String|错误码|
|**message**|String|错误消息|
### RespPackageResult
|名称|类型|描述|
|---|---|---|
|**remainder**|Long|剩余条数|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|INVALID_ARGUMENT|
|**500**|INTERNAL|
