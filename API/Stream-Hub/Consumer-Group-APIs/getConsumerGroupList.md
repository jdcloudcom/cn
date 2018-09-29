# getConsumerGroupList


## 描述
查看指定主题的所有消费组

## 请求方式
GET

## 请求地址
https://streambus.jdcloud-api.com/v1/regions/{regionId}/consumerGroupList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**topicId**|Integer|True| |主题id|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**consumerGroup**|Object[]| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|UNAUTHENTICATED|
