# getHardwareStack


## 描述
硬件配置信息列表

## 请求方式
GET

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/hardwareStack

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

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
|**data**|HardWareStackData|查询的硬件信息|
|**message**|String| |
|**status**|String| |
### HardWareStackData
|名称|类型|描述|
|---|---|---|
|**disk**|Disk[]| |
|**scale**|Scale[]| |
### Disk
|名称|类型|描述|
|---|---|---|
|**limit**|String|最大磁盘容量|
|**volumeType**|String|磁盘容量类型|
### Scale
|名称|类型|描述|
|---|---|---|
|**core**|Integer|CPU核数|
|**memory**|Integer|内存大小，单位G|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
