# createPipeline


## 描述
新建流水线任务

## 请求方式
POST

## 请求地址
https://pipeline.jdcloud-api.com/v1/regions/{regionId}/pipeline

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**data**|PipelineParams|False| | |

### PipelineParams
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |流水线的名称|
|**content**|String|True| |流水线定义的json字符串。因为配置灵活且会支持用户直接上传json配置文件的方式配置，所以不对其在提交和显示的时候做解析或反解析。|
|**method**|String|False| |创建方式， 值为CREATE_DEMO时，为创建流水线demo|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**uuid**|String|流水线任务uuid|
|**result**|Boolean|创建成功则是true|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
