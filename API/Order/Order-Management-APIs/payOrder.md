# payOrder


## 描述
订单支付

## 请求方式
POST

## 请求地址
https://order.jdcloud-api.com/v2/regions/{regionId}/order/{orderNumber}:pay

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|
|**orderNumber**|String|True| |orderNumber ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**autoPay**|Boolean|False| |自动支付标示，当为true,才会发生自动支付，后付费的订单直接支付0元，预付费的订单（余额+代金劵）> 订单应付金额，成功，否则支付失败（建议到京东云平台用现金方式支付）|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**orderNumber**|String|订单号|
|**autoPay**|Boolean|自动支付标示，当为true,才会发生自动支付，后付费的订单直接支付0元，预付费的订单（余额+代金劵）> 订单应付金额，成功，否则支付失败（建议到京东云平台用现金方式支付）|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
