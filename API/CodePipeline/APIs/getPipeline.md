# getPipeline


## 描述
根据uuid获取流水线任务的配置信息

## 请求方式
GET

## 请求地址
https://pipeline.jdcloud-api.com/v1/regions/{regionId}/pipeline/{uuid}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**uuid**|String|True| |流水线 uuid|
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
|**pipeline**|Pipeline| |
### Pipeline
|名称|类型|描述|
|---|---|---|
|**uuid**|String|流水线的uuid|
|**createdAt**|Integer|流水线创建时间戳|
|**updatedAt**|Integer|流水线最后一次更新时间戳|
|**name**|String|流水线的名称|
|**content**|String|流水线定义的json字符串。因为配置灵活且会支持用户直接上传json配置文件的方式配置，所以不对其在提交和显示的时候做解析或反解析。|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
