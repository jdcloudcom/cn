# queryResourceBills


## 描述
查询资源账单列表

## 请求方式
POST

## 请求地址
https://billing.jdcloud-api.com/v1/regions/{regionId}/resourceBills

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**appCode**|String|False| |appCode|
|**billingType**|Integer|False| |billingType|
|**endTime**|String|False| |endTime|
|**ignoreZero**|Integer|False| |ignoreZero|
|**pageIndex**|Integer|False| |pageIndex|
|**pageSize**|Integer|False| |pageSize|
|**payState**|Integer|False| |payState|
|**payType**|Integer|False| |payType|
|**queryType**|Integer|False| |查询类别   1：资源账单   2：消费记录|
|**region**|String|False| |region|
|**resourceId**|String|False| |resourceId|
|**role**|Integer|False| |role|
|**serviceCode**|String|False| |serviceCode|
|**site**|Integer|False| |site|
|**startTime**|String|False| |startTime|
|**timeType**|Integer|False| |timeType|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**pagination**|Pagination| |
|**result**|ResourceBillQueryResultItem[]| |
### Pagination
|名称|类型|描述|
|---|---|---|
|**currPageNo**|Integer|当前页|
|**numberPages**|Integer|页数|
|**numberRecords**|Integer|每页记录数|
|**pageSize**|Integer|页面大小|
|**startIndex**|Integer|起始页|
### ResourceBillQueryResultItem
|名称|类型|描述|
|---|---|---|
|**appCode**|String|appCode|
|**arrearFee**|Number|欠费金额|
|**balancePayFee**|Number|余额支付金额|
|**billEndTime**|String|账单结束时间|
|**billId**|Number|账单id|
|**billStartTime**|String|账单开始时间|
|**billingType**|Integer|计费类型|
|**billingTypeName**|String|计费类型描述|
|**cashCouponPayFee**|Number|代金券支付金额|
|**cashPayFee**|Number|现金支付金额|
|**endTime**|String|结束时间|
|**opTypeName**|String|1：新购 2：续费 3：配置变更|
|**pin**|String|用户pin|
|**region**|String|区域|
|**regionName**|String|区域名称|
|**resourceId**|String|资源id|
|**resourceName**|String|资源名称|
|**serviceCode**|String|serviceCode|
|**serviceCodeName**|String|serviceCodeName|
|**settleTime**|String|结算日期|
|**startTime**|String|开始时间|
|**systemType**|Integer|1：老计费 2：新计费|
|**timeSpan**|Integer|时间|
|**timeSpanName**|String|时间|
|**timeUnit**|Integer|时间单位|
|**timeUnitName**|String|时间单位名称 1：小时 2：天 3：月 4：年|
|**totalFee**|Number|总金额|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
