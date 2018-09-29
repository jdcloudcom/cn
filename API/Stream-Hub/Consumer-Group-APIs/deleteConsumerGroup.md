# deleteConsumerGroup


## 描述
删除consumerGroupName

## 请求方式
DELETE

## 请求地址
https://streambus.jdcloud-api.com/v1/regions/{regionId}/consumerGroup

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**consumerGroupId**|Integer|True| |消费组ID|
|**topicId**|Integer|True| |主题ID|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**message**|String| |
|**status**|Boolean| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**401**|STREAMHUB_UNAUTHENTICATED|
|**400**|UNAUTHENTICATED|
