# setOnlineBillingType


## 描述
设置线上计费方式

## 请求方式
POST

## 请求地址
https://cdn.jdcloud-api.com/v1/onlineBillingType


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**allType**|Integer|False| |计费方式,取值[0,1],0:日流量计费,1:日峰值带宽计费.|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Object| |
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
