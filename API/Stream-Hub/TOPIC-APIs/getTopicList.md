# getTopicList


## 描述
查询topic列表，返回topic的集合

## 请求方式
GET

## 请求地址
https://streambus.jdcloud-api.com/v1/regions/{regionId}/topicList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**keyword**|String|False| | |


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**topic**|Object[]| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**401**|ERROR|
