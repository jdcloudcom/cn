# describeDeviceRaids


## 描述
查询某种实例类型的云物理服务器支持的RAID类型，可查询系统盘RAID类型和数据盘RAID类型

## 请求方式
GET

## 请求地址
https://cps.jdcloud-api.com/v1/regions/{regionId}/raids

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeRegiones）获取云物理服务器支持的地域|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**deviceType**|String|True| |实例类型，可调用（describeDeviceTypes）接口获取指定地域的实例类型，例如：cps.c.normal|
|**volumeType**|String|False| |磁盘类型，取值范围：system、data|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**raids**|Raid[]| |
### Raid
|名称|类型|描述|
|---|---|---|
|**description**|String|RAID类型描述|
|**deviceType**|String|云物理服务器类型, 如 cps.c.normal|
|**raidType**|String|RAID类型, 如 NORAID, RAID0, RAID1|
|**raidTypeId**|String|RAID类型ID|
|**volumeDetail**|String|设备详情|
|**volumeType**|String|磁盘类型, 如 system/data|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Bad request|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
