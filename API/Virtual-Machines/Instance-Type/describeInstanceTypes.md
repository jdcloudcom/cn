# describeInstanceTypes


## 描述
查询实例规格信息列表


## 请求方式
GET

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/instanceTypes

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**filters**|Filter[]|False| |instanceTypes - 实例规格，精确匹配，支持多个<br>az - 可用区，精确匹配，支持多个<br>|

### Filter
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**instanceTypes**|InstanceType[]|通用的实例规格|
|**specificInstanceTypes**|InstanceType[]|用户特有的实例规格；需要工单申请|
|**totalCount**|Integer|总数量|
### InstanceType
|名称|类型|描述|
|---|---|---|
|**cpu**|Integer|cpu个数|
|**desc**|String|描述|
|**family**|String|实例规格类型|
|**gpu**|Gpu|Gpu配置|
|**instanceType**|String|实例规格，比如g.b1.2xlarge|
|**localDisks**|LocalDisk[]|本地缓存盘配置，目前只有Gpu规格上才有|
|**memoryMB**|Integer|内存大小|
|**nicLimit**|Integer|支持弹性网卡的数量|
|**state**|InstanceTypeState[]|规格状态|
### Gpu
|名称|类型|描述|
|---|---|---|
|**model**|String|GPU型号|
|**number**|Integer|GPU数量|
### LocalDisk
|名称|类型|描述|
|---|---|---|
|**diskSizeGB**|Integer|磁盘大小|
|**diskType**|String|磁盘类型，取值范围{premium-hdd, ssd}|
### InstanceTypeState
|名称|类型|描述|
|---|---|---|
|**az**|String|可用区|
|**inStock**|Boolean|可售卖情况，true:可售卖、false:已售罄不可用|

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
