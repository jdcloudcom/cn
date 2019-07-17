# startPipeline


## 描述
根据uuid启动一个流水线任务

## 请求方式
POST

## 请求地址
https://pipeline.jdcloud-api.com/v1/regions/{regionId}/pipeline/{uuid}:start

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**uuid**|String|True| |流水线uuid|
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
|**instanceUuid**|String|本次执行生成的实例的uuid|
|**uuid**|String|提交运行的流水线uuid|
|**result**|Boolean|提交任务是否成功|

## 返回码
|返回码|描述|
|---|---|
|**200**|ok|
