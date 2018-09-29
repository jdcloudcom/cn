# modifyEPB


## 描述
更新实例弹性防护带宽

## 请求方式
POST

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:modifyEPB

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |实例 ID|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ePBSpec**|EPBSpec|True| |更新弹性防护带宽请求参数|

### EPBSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ePB**|Integer|False| |弹性防护带宽|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
