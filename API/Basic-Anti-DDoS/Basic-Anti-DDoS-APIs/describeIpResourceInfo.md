# describeIpResourceInfo


## 描述
查询公网Ip基本信息

## 请求方式
GET

## 请求地址
https://baseanti.jdcloud-api.com/v1/regions/{regionId}/ipResources/{ip}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ip**|String|True||公网ip|
|**regionId**|String|True||Region ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**data**|[IpResourceInfo](##IpResourceInfo)||
### <a name="IpResourceInfo">IpResourceInfo</a>
|名称|类型|描述|
|---|---|---|
|**blackHoleThreshold**|Integer|黑洞阈值，单位bps|
|**cleanThresholdBps**|Integer|触发清洗的流量速率，单位bps|
|**cleanThresholdPps**|Integer|触发清洗的包速率，单位pps|
|**ip**|String|公网IP|
|**region**|String|地域，cn-north-1、cn-south-1、cn-east-1、cn-east-2|
|**safeStatus**|Integer|0->安全 1->清洗 2->黑洞|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
