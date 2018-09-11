# wfInstanceDetail


## 描述
查看指定工作流详情信息

## 请求方式
POST

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/wfInstance:detail

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**wfId**|String|True|||
|**wfInstanceId**|String|True|||


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**message**|[Message](##Message)||
### <a name="Message">Message</a>
|名称|类型|描述|
|---|---|---|
|**code**|String|编码|
|**data**|Object|数据|
|**instanceId**|String||
|**jobId**|String|作业ID|
|**path**|[Path[]](##Path)||
|**pipeline**|String||
|**rect**|[Rect[]](##Rect)||
|**result**|String|结果|
|**source**|String||
|**sourceParameterList**|String[]||
|**target**|String||
|**targetParameterList**|String[]||
|**taskId**|String||
|**total**|Integer||
### <a name="Path">Path</a>
|名称|类型|描述|
|---|---|---|
|**child**|Integer||
|**father**|Integer||
### <a name="Rect">Rect</a>
|名称|类型|描述|
|---|---|---|
|**instanceId**|Integer||
|**instanceStatus**|Integer||
|**intervalTimes**|Integer|失败任务再次运行间隔|
|**jobId**|Integer||
|**retryTimes**|Integer|任务失败重试次数|
|**taskDesc**|String||
|**taskId**|String||
|**taskName**|String||
|**taskType**|String||
|**x**|Number||
|**y**|Number||

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
