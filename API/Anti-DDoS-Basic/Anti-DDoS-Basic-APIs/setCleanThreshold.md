# setCleanThreshold


## 描述
设置公网IP的清洗阈值

## 请求方式
POST

## 请求地址
https://baseanti.jdcloud-api.com/v1/regions/{regionId}/ipResources/{ip}:setCleanThreshold

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ip**|String|True| |公网IP地址|
|**regionId**|String|True| |所属地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cleanThresholdSpec**|CleanThresholdSpec|True| |cc参数|

### CleanThresholdSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cleanThresholdBps**|Integer|False| |触发清洗的流量速率，单位bps，范围是10000000到300000000|
|**cleanThresholdPps**|Integer|False| |触发清洗的包速率，单位pps，范围是2000到70000|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
