# getResourceName


## 描述
查询用于在账单展示的资源名称信息

## 请求方式
GET

## 请求地址
https://billing.jdcloud-api.com/v1/regions/{regionId}/resourceOrder/{resourceId}/resourceName

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| | |
|**resourceId**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**region**|String|False| | |
|**serviceCode**|String|False| | |


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**resourceName**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
