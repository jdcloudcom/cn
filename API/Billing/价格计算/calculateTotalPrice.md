# calculateTotalPrice


## 描述
查询计费价格信息

## 请求方式
POST

## 请求地址
https://billing.jdcloud-api.com/v1/regions/{regionId}/calculateTotalPrice

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clientType**|Integer|False| |客户端：1.PC端；2.移动端；|
|**cmd**|Integer|True| |操作类型 1:创建 2:续费 3:升配 4:删除|
|**operateTime**|String|False| |操作时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**orderList**|OrderPriceProtocol[]|False| |计算价格的订单|
|**packageCount**|Integer|True| |批量购买时数量|
|**promotionInfo**|String|False| |1:折扣（不需要传） 2:免费活动3:付费活动 4:推荐码 5:会员价 [{"promotionType":1,"activityCode":123},{"promotionType":2,"activityCode":}]|

### OrderPriceProtocol
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**appCode**|String|False| |业务线|
|**billingType**|Integer|False| |计费类型 1:按配置 2:按用量 3:包年包月|
|**count**|Integer|False| |具体商品数量，默认为1|
|**formula**|Formula[]|False| |计算公式（配置细项）|
|**formulaStr**|String|False| |配置细项|
|**networkOperator**|Integer|False| |网络类型 0:non 1:非BGP  2:BGP|
|**pin**|String|False| |用户pin|
|**region**|String|False| |地域|
|**resourceId**|String|False| |资源id|
|**serviceCode**|String|False| |产品线|
|**site**|Integer|False| |站点信息 0：主站  其他：专有云|
|**sourceId**|String|False| |交易单模块sourceId|
|**startTime**|String|False| |订单开始时间|
|**taskId**|String|False| |自然单列表|
|**timeSpan**|Integer|False| |时长|
|**timeUnit**|Integer|False| |时长类型 0:无(非包年包月) 1:小时 2:天 3:月 4:年|
### Formula
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**key**|String|False| |计费项别名|
|**number**|Number|False| |计费项数量|
|**unit**|String|False| |单位|
|**value**|Number|False| |用量|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**discountedTotalPrice**|Number|折扣后订单价格|
|**favorableInfos**|String|参与优惠的明细|
|**list**|OrderPriceDetail[]|计算完价格后的详细订单列表|
|**remark**|String|备注|
|**totalDiscount**|Number|总折扣金额|
|**totalOriginalPrice**|Number|订单原价 包年时 一年原价为12个月价格，totalPrice为10个月价格|
|**totalPrice**|Number|订单折扣前总价|
|**totalPriceScale4**|Number|订单折扣前总价4位|
|**totalUnitPrice**|String|各订单单价总和|
### OrderPriceDetail
|名称|类型|描述|
|---|---|---|
|**appCode**|String|业务线|
|**billingType**|Integer|计费类型1:按配置2:按用量3:包年包月|
|**discount**|Number|折扣金额|
|**discountedPrice**|Number|折扣后订单金额|
|**endTime**|String|结束时间|
|**favorableInfo**|String|FavorableInfo转成json后的字符串|
|**formula**|Formula[]|配置信息|
|**networkOperator**|Integer|网络类型 0:non1:非BGP2:BGP|
|**originalPrice**|Number|订单原价 包年时 一年原价为12个月价格，totalPrice为10个月价格|
|**pin**|String|用户pin|
|**price**|Number|折扣前总价|
|**priceScale4**|Number|四位小数价格|
|**priceSnapShot**|String|价格快照|
|**processType**|Integer|变配明细（1-升配补差价，2-降配延时）|
|**region**|String|地域|
|**resourceId**|String|资源id|
|**serviceCode**|String|产品线|
|**site**|Integer|站点  0:主站  其他:专有云|
|**sourceId**|String|交易单模块sourceId|
|**startTime**|String|开始时间|
|**taskId**|String|自然单列表|
|**timeSpan**|Integer|时长|
|**timeUnit**|Integer|时长类型 1:小时2:天3:月4:年|
### Formula
|名称|类型|描述|
|---|---|---|
|**key**|String|计费项别名|
|**number**|Number|计费项数量|
|**unit**|String|单位|
|**value**|Number|用量|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
