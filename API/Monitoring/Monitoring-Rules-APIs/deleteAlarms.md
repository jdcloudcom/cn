# deleteAlarms


## 描述
批量删除已创建的报警规则

## 请求方式
DELETE

## 请求地址
https://monitor.jdcloud-api.com/v1/regions/{regionId}/alarms

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ids**|String|True| |待删除的规则id，多个规则之间用"\|"间隔|


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
