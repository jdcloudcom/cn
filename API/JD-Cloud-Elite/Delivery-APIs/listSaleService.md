# listSaleService


## 描述
分页查询交付单信息

## 请求方式
GET

## 请求地址
https://elite.cn-south-1.jdcloud-api.com/v1/regions/{regionId}/listSaleService

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNo**|Integer|True| |页码（最小1）|
|**pageSize**|Integer|True| |每页记录数（最小10，最大100）|
|**deliverNumber**|String|False| |交付单号|
|**deliverStatus**|Integer|False| |交付状态|
|**createDtStart**|String|False| |交付单创建起始时间，格式：yyyy-MM-dd HH:mm:ss|
|**createDtEnd**|String|False| |交付单创建结束时间，格式：yyyy-MM-dd HH:mm:ss|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|请求ID，每次请求都不一样|

### Result
|名称|类型|描述|
|---|---|---|
|**status**|Boolean|true为成功，false为失败|
|**message**|String|描述信息|
|**data**|ProductServiceVoListData|查询数据结果|
### ProductServiceVoListData
|名称|类型|描述|
|---|---|---|
|**pageNo**|Integer|页码|
|**pageSize**|Integer|每页记录数|
|**totalRecord**|Integer|总记录数|
|**totalPage**|Integer|总页数|
|**dataList**|ProductServiceVo[]|交付单信息列表|
### ProductServiceVo
|名称|类型|描述|
|---|---|---|
|**deliverNumber**|String|交付单号|
|**orderNumber**|String|订单号|
|**productId**|Integer|产品ID|
|**skuId**|Integer|sku ID|
|**skuName**|String|sku名称|
|**serviceCode**|String|服务code|
|**num**|Integer|数量|
|**period**|Integer|周期|
|**periodType**|Integer|周期类型|
|**periodTypeName**|String|周期类型名称|
|**accountNum**|Integer|账号数量|
|**deliverStatus**|Integer|交付状态|
|**deliverStatusName**|String|交付状态名称|
|**effectiveDt**|String|服务生效时间，格式：yyyy-MM-dd HH:mm:ss|
|**failureDt**|String|服务过期时间，格式：yyyy-MM-dd HH:mm:ss|
|**extraInfo**|String|商品属性|
|**remark**|String|交付单备注|
|**orderTotalFee**|String|订单金额|
|**orderActualFee**|String|订单实付金额|
|**paymentDt**|String|订单支付时间|
|**extraChargeInfo**|String|额外计费项信息|
|**orderItemExtraChargeInfos**|OrderItemExtraChargeInfo[]|额外计费详情信息|
### OrderItemExtraChargeInfo
|名称|类型|描述|
|---|---|---|
|**name**|String|购买用户pin|
|**unit**|String|单位|
|**buyNum**|Integer|购买数量|
|**sellingPrice**|String|销售价格|
|**settlementPrice**|String|结算价格|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|

