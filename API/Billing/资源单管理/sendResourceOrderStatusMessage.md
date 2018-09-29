# sendResourceOrderStatusMessage


## 描述
删除资源

## 请求方式
POST

## 请求地址
https://billing.jdcloud-api.com/v1/regions/{regionId}/sendResourceOrderStatusMessage

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cmd**|Integer|True| |操作类型 4:删除|
|**operateTime**|String|False| |操作时间|
|**operatorName**|String|True| |操作人 用户:用户pin 管理员:操作人erp|
|**operatorType**|Integer|True| |操作者类型 0：用户 1：管理员（运营）|
|**orderList**|ResourceOrderStatusVo[]|False| |资源单信息|

### ResourceOrderStatusVo
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**billingStatus**|Integer|False| |计费状态 0:停止计费 1:计费中|
|**billingType**|Integer|False| |计费类型 1:按配置 2:按用量 3:包年包月|
|**chargeDuration**|Integer|False| |timeSpan兼容交易系统字段|
|**chargeMode**|Integer|False| |billingType兼容交易系统字段|
|**chargeUnit**|Integer|False| |timeUnit兼容交易系统字段|
|**endTime**|String|False| |结束时间|
|**operateTime**|String|False| |操作时间|
|**pin**|String|True| |用户pin|
|**resourceId**|String|True| |资源id|
|**site**|Integer|False| |站点信息 0:中国 1:国际  10:专有云|
|**status**|Integer|False| |资源状态 1:正常 2:停服 3:删除|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**result**|Boolean|结果|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
