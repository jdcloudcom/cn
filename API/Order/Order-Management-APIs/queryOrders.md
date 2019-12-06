# queryOrders


## 描述
查询订单列表

## 请求方式
POST

## 请求地址
https://order.jdcloud-api.com/v2/regions/{regionId}/orders

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域编码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**queryVo**|ListOrderRequest|False| | |

### ListOrderRequest
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**appCode**|String|False| |业务线|
|**chargeMode**|String|False| |计费类型(CONFIG-按配置,FLOW-按用量MONTHLY-包年包月,ONCE-按次付费)|
|**startTime**|Long|False| |查询订单开始时间戳,（开始时间和结束时间最大跨度为一年，如都不传默认为一个月）|
|**endTime**|Long|False| |查询订单结束时间戳,（开始时间和结束时间最大跨度为一年，如都不传默认为一个月）|
|**orderType**|String|False| |购买订单类型(NEW-新购,RENEW-续费,RESIZE_FORMULA-配置变更,TEMP_UPGRADE-临时升配)|
|**pageNumber**|Integer|False| |分页：订单第几页|
|**pageSize**|Integer|False| |分页：订单条数|
|**payType**|String|False| |付费类型(PRE_PAID-预付费,POST_PAID-后付费)|
|**serviceCode**|String|False| |产品线|
|**status**|String|False| |订单状态（PAID-已支付,CANCELED-已取消,NO_PAY-未支付,FAILED-失败,DEALING-处理中,REFUND_PART-部分退款,REFUND_ALL-全部退款）|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**resultList**|OrderResponseObject[]| |
|**totalCount**|Integer| |
|**totalPage**|Integer| |
### OrderResponseObject
|名称|类型|描述|
|---|---|---|
|**actualFee**|Number|订单应付金额|
|**appCode**|String|业务线|
|**appName**|String|业务名称|
|**chargeMode**|String|计费类型(CONFIG-按配置,FLOW-按用量MONTHLY-包年包月,ONCE-按次付费)|
|**createTime**|String|订单创建时间（格式：yyyy-MM-dd HH:mm:ss）|
|**discountFee**|Number|折扣金额|
|**orderNumber**|String|订单号|
|**orderType**|String|购买订单类型(NEW-新购,RENEW-续费，RESIZE_FORMULA-配置变更)|
|**payTime**|String|订单支付时间（格式：yyyy-MM-dd HH:mm:ss）|
|**payType**|String|付费类型(PRE_PAID-预付费,POST_PAID-后付费)|
|**paymentNumber**|String|订单号|
|**pin**|String|用户pin|
|**selfSupportType**|String|自营类型(SELF_SUPPORT-自营,THIRD_PARTY_SUPPORT-非自营)|
|**serviceName**|String|产品线名称|
|**status**|String|订单状态（PAID-已支付,FAILED-失败,NO_PAY-未支付,DEALING-处理中,CANCELED-已取消,REFUND_PART-部分退款,REFUND_ALL-全部退款）|
|**totalFee**|Number|订单总金额|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
