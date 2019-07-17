# deletePipeline


## 描述
删除一个流水线任务

## 请求方式
DELETE

## 请求地址
https://pipeline.jdcloud-api.com/v1/regions/{regionId}/pipeline/{uuid}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**uuid**|String|True| |流水线任务uuid|
|**regionId**|String|True| |Region ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**uuid**|String|流水线任务uuid|
|**result**|Boolean|删除成功则是true|

## 返回码
|返回码|描述|
|---|---|
|**200**|ok|
