# queryConsumeRecords


## 描述
查询资源账单详情

## 请求方式
POST

## 请求地址
https://billing.jdcloud-api.com/v1/regions/{regionId}/resourceBills/{resourceId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| | |
|**resourceId**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**appCode**|String|False| | |
|**billingType**|Integer|False| | |
|**endTime**|String|False| | |
|**ignoreZero**|Integer|False| | |
|**payState**|Integer|False| | |
|**payType**|Integer|False| | |
|**queryType**|Integer|False| | |
|**region**|String|False| | |
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
|**result**|ConsumeRecord[]| |
### Pagination
|名称|类型|描述|
|---|---|---|
|**currPageNo**|Integer|当前页|
|**numberPages**|Integer|页数|
|**numberRecords**|Integer|每页记录数|
|**pageSize**|Integer|页面大小|
|**startIndex**|Integer|起始页|
### ConsumeRecord
|名称|类型|描述|
|---|---|---|
|**appCode**|String|appCode|
|**billFee**|Number|账单金额|
|**billFee2**|Number|账单金额保留小数点后2位|
|**billingRecordId**|Integer|消费记录id|
|**billingType**|Integer|计费类型|
|**couponFee**|Number|优惠金额|
|**couponId**|String|优惠券id|
|**createTime**|String|创建日期|
|**discountFee**|Number|折扣金额|
|**endTime**|String|结束时间|
|**formula**|String|规格|
|**id**|Number|消费记录数据库唯一id|
|**isBillGenerated**|Integer| |
|**pin**|String|用户pin|
|**priceSnapShot**|String|价格快照|
|**refundNo**|String|退款单号|
|**region**|String|区域|
|**resourceId**|String|资源id|
|**serviceCode**|String|serviceCode|
|**startTime**|String|开始时间|
|**subBillId**|Number|子账单id|
|**transactionNo**|String|交易单号|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
