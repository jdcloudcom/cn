# describeInstanceRaid


## 描述
查询单个云物理服务器已安装的RAID信息，包括系统盘RAID信息和数据盘RAID信息

## 请求方式
GET

## 请求地址
https://cps.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:describeInstanceRaid

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
|**dataRaidType**|String|数据盘RAID类型|
|**dataRaidTypeId**|String|数据盘RAID类型ID|
|**sysRaidType**|String|系统盘RAID类型|
|**sysRaidTypeId**|String|系统盘RAID类型ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Bad request|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
