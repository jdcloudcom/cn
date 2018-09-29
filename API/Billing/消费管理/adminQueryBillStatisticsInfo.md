# adminQueryBillStatisticsInfo


## 描述
查询消费统计信息

## 请求方式
POST

## 请求地址
https://billing.jdcloud-api.com/v1/regions/{regionId}/accounting/adminQueryBillStatisticsInfo

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**appCode**|String|False| |应用码|
|**billingType**|Integer|False| |付费类型|
|**endTime**|String|False| |结束时间|
|**ignoreZero**|Integer|False| | |
|**payState**|Integer|False| |付费状态|
|**payType**|Integer|False| |付费类型|
|**pin**|String|False| |用户pin|
|**queryType**|Integer|False| |查询类别   1：资源账单   2：消费记录|
|**region**|String|False| |区域|
|**resourceId**|String|False| |资源ID|
|**role**|Integer|False| |角色|
|**serviceCode**|String|False| |服务码|
|**site**|Integer|False| |站点|
|**startTime**|String|False| |开始时间|
|**timeType**|Integer|False| |1: 按账期 2：按消费时间|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**billStatisticsInfoVo**|BillStatisticsInfoVo| |
### BillStatisticsInfoVo
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
