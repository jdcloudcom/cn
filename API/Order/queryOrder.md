# queryOrder


## 描述
查询订单详情

## 请求方式
GET

## 请求地址
https://order.jdcloud-api.com/v2/regions/{regionId}/order/{orderNumber}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|
|**orderNumber**|String|True| |orderNumber ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**includeDetail**|Boolean|False| |是否包含商品详情|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|OrderDetailResponseObject| |
### OrderDetailResponseObject
|名称|类型|描述|
|---|---|---|
|**appCode**|String|业务线|
|**appName**|String|业务线名称|
|**balancePay**|Number|余额支付金额|
|**discountFee**|Number|折扣金额|
|**refundFee**|Number|退款金额|
|**favorableFee**|Number|代金券金额|
|**totalFee**|Number|订单总金额|
|**moneyPay**|Number|现金支付金额|
|**actualFee**|Number|应付金额（订单总金额-折扣金额）|
|**paidFee**|Number|已支付总额|
|**activityType**|String|活动订单类型(NORMAL-正常订单,ACTIVITY-活动订单)|
|**chargeMode**|String|计费类型(CONFIG-按配置,FLOW-按用量MONTHLY-包年包月,ONCE-按次付费)|
|**createTime**|String|订单创建时间（格式：yyyy-MM-dd HH:mm:ss）|
|**expirationTime**|String|未支付订单自动取消时间（格式：yyyy-MM-dd HH:mm:ss）|
|**orderNumber**|String|订单号|
|**orderType**|String|购买订单类型(NEW-新购,RENEW-续费，RESIZE_FORMULA-配置变更)|
|**payTime**|String|订单支付时间（格式：yyyy-MM-dd HH:mm:ss）|
|**payType**|String|付费类型(PRE_PAID-预付费,POST_PAID-后付费)|
|**payUrl**|String|支付确认页地址|
|**payer**|String|付款人|
|**paymentChannel**|String|支付渠道（BALANCE_PAYMENT-余额支付,ENTERPRISE_BANK_PAYMENT-企业网银,PERSONAL_BANK_PAYMENT-个人网银,JD_PAYMENT-京东,WENXIN_PAYMENT-微信支付,OFFLINE_PAYMENT-线下汇款）|
|**paymentNumber**|String|支付订单号|
|**pin**|String|用户pin|
|**proposer**|String|订单申请人，创建人|
|**remark**|String|备注|
|**selfSupportType**|String|自营类型(SELF_SUPPORT-自营,THIRD_PARTY_SUPPORT-非自营)|
|**serviceName**|String|产品线名称|
|**siteType**|String|站点名称（MAIN_SITE-主站，INTERNATIONAL_SITE-国际站，SUQIAN_DEDICATED_CLOUD-宿迁专有云）|
|**status**|String|订单状态（PAID-已支付,FAILED-失败,NO_PAY-未支付,DEALING-处理中,CANCELED-已取消,REFUND_PART-部分退款,REFUND_ALL-全部退款）|
|**updatedTime**|String|订单更新时间|
|**childOrderDetailList**|OrderDetailResponseObject[]|子订单|
|**orderItemDetails**|OrderItemDetailResponseObject[]|子资源订单|
### OrderItemDetailResponseObject
|名称|类型|描述|
|---|---|---|
|**totalFee**|Number|订单总金额|
|**actualFee**|Number|应付金额（订单总金额-折扣金额）|
|**balancePay**|Number|余额支付金额|
|**chargeDuration**|Integer|计费时长|
|**moneyPay**|Number|现金支付金额|
|**refundFee**|Number|退款金额|
|**chargeMode**|String|计费类型(CONFIG-按配置,FLOW-按用量MONTHLY-包年包月,ONCE-按次付费)|
|**createTime**|String|订单创建时间（格式：yyyy-MM-dd HH:mm:ss）|
|**expireDateAfter**|String|续费后资源到期时间（格式：yyyy-MM-dd HH:mm:ss）|
|**expireDateBefore**|String|续费前资源到期时间（格式：yyyy-MM-dd HH:mm:ss）|
|**extraInfo**|ExtraInfo[]|销售属性|
|**extraInfoAfter**|ExtraInfo[]|续费后资源到期-销售属性|
|**extraInfoBefore**|ExtraInfo[]|续费前资源到期-销售属性|
|**favorableFee**|Number|代金券金额|
|**formula**|String|配置计费项|
|**itemId**|String|资源id|
|**itemName**|String|资源名称|
|**orderNumber**|String|订单号|
|**priceSnapshot**|String|价格快照|
|**quantity**|Integer|数量|
|**remark**|String|备注|
|**resizeFormulaType**|String|变配明细(UP-升配补差价，DOWN-降配延时,MODIFY_CONFIG-调整配置，RENEW-续费，RENEW_UP-续费升配，RENEW_DOWN-续费降配，MONTHLY-配置转包年包月，RENEW_FREE-补偿续费)|
|**serviceName**|String|产品名称|
|**siteType**|String|站点名称（MAIN_SITE-主站，INTERNATIONAL_SITE-国际站，SUQIAN_DEDICATED_CLOUD-宿迁专有云）|
|**status**|String|资源状态（CREATING-创建中,SUCCESS-成功,FAIL-失败）|
|**unit**|String|计费时长单位（HOUR-小时,DAY-天,MONTH-月,YEAR-年）|
|**orderItemDetailResponse**|OrderItemDetailResponseObject[]|子订单|
### ExtraInfo
|名称|类型|描述|
|---|---|---|
|**name**|String|名称|
|**value**|String|值|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
