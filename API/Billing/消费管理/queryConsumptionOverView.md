# queryConsumptionOverView


## 描述
查询消费总览

## 请求方式
GET

## 请求地址
https://billing.jdcloud-api.com/v1/regions/{regionId}/consumeOverView

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**endTime**|String|True| | |
|**startTime**|String|True| | |
|**timeType**|Integer|True| | |


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**actualFee**|Number| |
|**arrearFee**|Number| |
|**balancePayFee**|Number| |
|**cashCouponPayFee**|Number| |
|**cashPayFee**|Number| |
|**consumptionList**|Map| |
|**consumptionProductVoList**|ConsumptionProduct[]| |
|**endTime**|String| |
|**pin**|String| |
|**startTime**|String| |
### ConsumptionProduct
|名称|类型|描述|
|---|---|---|
|**actualFee**|Number|优惠后金额|
|**appCode**|String|appCode|
|**appCodeName**|String|appCodeName|
|**arrearFee**|Number|欠费金额|
|**balancePayFee**|Number|余额支付|
|**cashCouponPayFee**|Number|代金券支付金额|
|**cashPayFee**|Number|现金支付|
|**productDetailList**|Map| |
|**productDetails**|Consumption[]| |
|**serviceCode**|String|serviceCode|
|**serviceCodeName**|String|serviceCodeName|
### Consumption
|名称|类型|描述|
|---|---|---|
|**actualFee**|Number|优惠后金额|
|**arrearFee**|Number|欠费金额|
|**balancePayFee**|Number|余额支付|
|**billingType**|Integer|计费类型|
|**cashCouponPayFee**|Number|优惠券支付金额|
|**cashPayFee**|Number|现金支付|
|**payType**|Integer|支付类型|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
