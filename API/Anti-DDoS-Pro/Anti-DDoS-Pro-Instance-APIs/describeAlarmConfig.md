# describeAlarmConfig


## 描述
查询告警配置

## 请求方式
GET

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:describeAlarmConfig

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |实例 ID|
|**regionId**|String|True| |Region ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|AlarmConfig| |
### AlarmConfig
|名称|类型|描述|
|---|---|---|
|**blackHoleAlarmEmailStatus**|Integer|黑洞告警邮件开关 0 关闭 1 开启|
|**blackHoleAlarmSmsStatus**|Integer|黑洞告警短信开关 0 关闭 1 开启|
|**blackHoleAlarmStatus**|Integer|黑洞告警总开关  0 关闭 1 开启|
|**ddosAlarmEmailStatus**|Integer|DDos 攻击告警邮件开关  0 关闭 1 开启|
|**ddosAlarmSmsStatus**|Integer|DDos 攻击告警短信开关  0 关闭 1 开启|
|**ddosAlarmStatus**|Integer|DDos 告警总开关 0 关闭 1 开启|
|**errorCodeAlarmStatus**|Integer|错误码告警总开关|
|**errorCodeDomain**|String[]|错误码告警域名列表|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
