# describeDeviceTypes


## 描述
查询云物理服务器实例类型

## 请求方式
GET

## 请求地址
https://cps.jdcloud-api.com/v1/regions/{regionId}/deviceTypes

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
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
|**deviceTypes**|DeviceType[]| |
### DeviceType
|名称|类型|描述|
|---|---|---|
|**cpuConcise**|String|CPU概要描述|
|**cpuDetail**|String|CPU详细信息|
|**dataDiskConcise**|String|数据磁盘概要信息|
|**dataDiskDetail**|String|数据磁盘详细信息|
|**gpuConcise**|String|GPU概要信息|
|**gpuDetail**|String|GPU详细信息|
|**ifConcise**|String|网口概要信息|
|**ifDetail**|String|网口详细信息|
|**memConcise**|String|内存概要信息|
|**memDetail**|String|内存详细信息|
|**nameEN**|String|实例类型英文名称, 如 cps.c.normal|
|**nameZH**|String|实例类型中文名称, 如 计算型|
|**region**|String|区域代码, 如 cn-east-1|
|**systemDiskConcise**|String|系统磁盘概要信息|
|**systemDiskDetail**|String|系统磁盘详细信息|
|**useTypeEN**|String|镜像类型英文描述, 如 standard|
|**useTypeZH**|String|镜像类型中文描述, 如 标准型|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Bad request|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
