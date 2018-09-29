# getInstanceList


## 描述
获取主机规格列表(过滤掉低内存的规格, 低于4核全部去掉。)

## 请求方式
GET

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/instances

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
|**data**|InstanceList[]|主机规格列表|
|**message**|String| |
|**status**|String| |
### InstanceList
|名称|类型|描述|
|---|---|---|
|**label**|String|机器型号的分类|
|**options**|Options[]| |
### Options
|名称|类型|描述|
|---|---|---|
|**label**|String|机器的CPU和内存大小|
|**value**|String|对应机器的规格描述|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
