# isArrear


## 描述
查询用户是否欠费

## 请求方式
GET

## 请求地址
https://billing.jdcloud-api.com/v1/regions/{regionId}/isArrear

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pin**|String|False| | |


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
