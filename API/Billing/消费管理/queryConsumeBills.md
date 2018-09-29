# queryConsumeBills


## 描述
查询消费记录列表

## 请求方式
POST

## 请求地址
https://billing.jdcloud-api.com/v1/regions/{regionId}/consumeBills

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**appCode**|String|False| | |
|**billingType**|Integer|False| | |
|**endTime**|String|False| | |
|**ignoreZero**|Integer|False| | |
|**pageIndex**|Integer|False| | |
|**pageSize**|Integer|False| | |
|**payState**|Integer|False| | |
|**payType**|Integer|False| | |
|**queryType**|Integer|False| | |
|**region**|String|False| | |
|**resourceId**|String|False| | |
|**role**|Integer|False| | |
|**serviceCode**|String|False| | |
|**site**|Integer|False| | |
|**startTime**|String|False| | |
|**timeType**|Integer|False| | |


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**pagination**|Pagination| |
|**result**|ConsumeBillQueryResultItem[]| |
### Pagination
|名称|类型|描述|
|---|---|---|
|**currPageNo**|Integer|当前页|
|**numberPages**|Integer|页数|
|**numberRecords**|Integer|每页记录数|
|**pageSize**|Integer|页面大小|
|**startIndex**|Integer|起始页|
### ConsumeBillQueryResultItem
|名称|类型|描述|
|---|---|---|
|**appCode**|String|appCode|
|**appCodeName**|String|appCodeName|
|**arrearFee**|Number|欠费金额|
|**balancePayFee**|Number|余额支付金额|
|**billEnd**|String|账单结束时间|
|**billFee**|Number|账单金额|
|**billId**|Number|账单id|
|**billStart**|String|账单开始时间|
|**billTime**|String|账单日期|
|**billingType**|Integer|计费类型|
|**billingTypeName**|String|计费类型描述|
|**cashCouponPayFee**|Number|代金券支付金额|
|**cashPayFee**|Number|现金支付金额|
|**createTime**|String|创建时间|
|**discountFee**|Number|折扣金额|
|**formula**|String|规格|
|**formulaStr**|String|规格|
|**payState**|Integer|支付状态|
|**pin**|String|用户pin|
|**region**|String|区域|
|**resourceId**|String|资源id|
|**serviceCode**|String|serviceCode|
|**serviceCodeName**|String|serviceCodeName|
|**settleTime**|String|结算时间|
|**systemType**|Integer|新老计费标识（1:老计费   2：新计费）|
|**totalFee**|Number|账单总额|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
