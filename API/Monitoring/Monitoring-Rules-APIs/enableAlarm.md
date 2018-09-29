# enableAlarm


## 描述
启用报警规则，当报警规则处于已禁用状态时，可以使用此接口启用报警规则。

## 请求方式
POST

## 请求地址
https://monitor.jdcloud-api.com/v1/regions/{regionId}/alarms/{alarmId}:enable

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**alarmId**|String|True| |规则id|
|**regionId**|String|True| |地域ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求的标识id|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|invalid parameter|
|**500**|internal server error|
