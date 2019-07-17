# stopPipelineInstance


## 描述
停止流水线的一次执行

## 请求方式
POST

## 请求地址
https://pipeline.jdcloud-api.com/v1/regions/{regionId}/pipeline/{uuid}/instance/{instanceUuid}:stop

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**uuid**|String|True| |流水线uuid|
|**instanceUuid**|String|True| |流水线执行的uuid|
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
|**instanceUuid**|String| |
|**actionUuid**|String| |
|**result**|Bool| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
