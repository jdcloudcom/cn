# getBillDetail


## 描述
查询消费记录详情

## 请求方式
GET

## 请求地址
https://billing.jdcloud-api.com/v1/regions/{regionId}/consumeBills/{billId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**billId**|Number|True| | |
|**regionId**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**systemType**|Integer|False| | |


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**actualFee**|Number| |
|**appCode**|String| |
|**appCodeName**|String| |
|**arrearFee**|Number| |
|**balancePayFee**|Number| |
|**billFee**|Number| |
|**billFee2**|Number| |
|**billId**|Number| |
|**billingType**|Integer| |
|**billingTypeName**|String| |
|**cashCouponFee**|Number| |
|**cashPayFee**|Number| |
|**couponFee**|Number| |
|**couponId**|String| |
|**createTime**|String| |
|**discountFee**|Number| |
|**endTime**|String| |
|**formula**|String| |
|**formulaStr**|String| |
|**paySate**|Integer| |
|**pin**|String| |
|**region**|String| |
|**resourceId**|String| |
|**resourceName**|String| |
|**serviceCode**|String| |
|**serviceCodeName**|String| |
|**site**|Integer| |
|**startTime**|String| |
|**systemType**|Integer| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
