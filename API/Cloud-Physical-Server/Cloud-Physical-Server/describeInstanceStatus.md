# describeInstanceStatus


## 描述
查询单个云物理服务器硬件监控信息

## 请求方式
GET

## 请求地址
https://cps.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:describeInstanceStatus

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |云物理服务器ID|
|**regionId**|String|True| |地域ID，可调用接口（describeRegiones）获取云物理服务器支持的地域|

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
|**cpus**|Boolean|CPU状态是否正常|
|**disks**|Boolean|硬盘状态是否正常|
|**mems**|Boolean|内存状态是否正常|
|**nics**|Boolean|网卡状态是否正常|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Bad request|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
