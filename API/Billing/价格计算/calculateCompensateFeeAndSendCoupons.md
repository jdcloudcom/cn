# calculateCompensateFeeAndSendCoupons


## 描述
计算赔偿金额并发放代金券

## 请求方式
POST

## 请求地址
https://billing.jdcloud-api.com/v1/regions/{regionId}/price/calculateCompensateFeeAndSendCoupons

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pin**|String|True| |用户pin|
|**resourceIds**|String[]|True| |资源ID|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**pin**|String|用户pin|
|**resourceList**|OrderCompensateFeeVo[]|订单信息|
|**totalCompensateFee**|Number|计算总价|
### OrderCompensateFeeVo
|名称|类型|描述|
|---|---|---|
|**appCode**|String|应用码|
|**billingType**|Integer|计费类型 1:按配置 2:按用量 3:包年包月 4:一次性|
|**endTime**|String|结束时间|
|**pin**|String|用户pin|
|**region**|String|资源区域|
|**resourceId**|String|资源id|
|**serviceCode**|String|服务码|
|**startTime**|String|开始时间|
|**totalFee**|Number|计算总价|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
