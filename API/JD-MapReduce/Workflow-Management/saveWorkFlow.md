# saveWorkFlow


## 描述
保存工作流的信息

## 请求方式
POST

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/workflow:save

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**workflow**|[EmrWorkflow](##EmrWorkflow)|True|||

### <a name="EmrWorkflow">EmrWorkflow</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**createTime**|String|False||工作流创建时间|
|**dataCenter**|String|False||数据中心，即regionId|
|**id**|Number|False|||
|**isSelfDependence**|Boolean|False||"是否自身依赖"<br>"1：自身依赖(默认)，0：非依赖"<br>|
|**isSendMsg**|Boolean|False||失败后是否发送通知|
|**modifyTime**|String|False||上一次修改时间|
|**status**|String|False||工作流状态|
|**taskScheduleType**|Integer|False||"0:即时任务(默认)"<br>"1：周期性任务"<br>"2：定时任务"<br>|
|**userpin**|String|False||用户名|
|**workflowId**|String|False||工作流ID|
|**workflowName**|String|False||工作流名称|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**data**|[Message](##Message)||
|**message**|String||
|**status**|String||
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
