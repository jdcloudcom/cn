# getSensitiveOpSetting


## 描述
获取操作保护设置信息

## 请求方式
GET

## 请求地址
https://sop.jdcloud-api.com/v1/regions/{regionId}/sensitiveOpSetting

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**action**|String|True| |操作action serviceName:actionName|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**extInfo**|String|扩展信息，type=1时为掩码后的手机号码 type=2时为掩码后的邮箱地址|
|**status**|Integer|操作保护启用状态：0-未启用, 1-已启用|
|**type**|Integer|操作保护验证方式：0-无, 1-短信, 2-邮箱, 3-MFA|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
