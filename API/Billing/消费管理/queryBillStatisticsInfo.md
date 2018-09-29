# queryBillStatisticsInfo


## 描述
查询资源账单，消费记录中的费用信息

## 请求方式
GET

## 请求地址
https://billing.jdcloud-api.com/v1/regions/{regionId}/billStatisticsInfo

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**appCode**|String|True| |appCode|
|**billingType**|Integer|True| |计费类型|
|**endTime**|String|True| |结束时间|
|**payState**|Integer|True| |支付状态|
|**payType**|Integer|True| |支付类型|
|**queryType**|Integer|True| |查询类型|
|**serviceCode**|String|True| |serviceCode|
|**startTime**|String|True| |开始时间|
|**timeType**|Integer|True| |时间类型|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**arrearFee**|Number|欠费金额|
|**balancePayFee**|Number|余额支付金额|
|**billFee**|Number|账单金额|
|**cashCouponPayFee**|Number|优惠券支付金额|
|**cashPayFee**|Number|现金支付金额|
|**discountFee**|Number|折扣金额|
|**totalFee**|Number|总金额|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
