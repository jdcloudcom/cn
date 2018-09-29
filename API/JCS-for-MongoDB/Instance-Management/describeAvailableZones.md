# describeAvailableZones


## 描述
获取可用区

## 请求方式
GET

## 请求地址
https://mongodb.jdcloud-api.com/v1/regions/{regionId}/availableZones

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**availableZones**|AvailableZones[]| |
### AvailableZones
|名称|类型|描述|
|---|---|---|
|**az**|String|可用区|
|**canSale**|Boolean|是否可售|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
