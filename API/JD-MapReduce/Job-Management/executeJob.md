# executeJob


## 描述
执行指定作业

## 请求方式
POST

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/job:execute

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clusterId**|String|True| |集群ID|
|**jmrTaskViewModel**|JmrTaskViewModel|True| |"需要传入参数: jobId、planId、workflowId、workflowInstanceId"<br>|

### JmrTaskViewModel
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataCenter**|String|False| |数据中心，即regionId|
|**duration**|String|False| |持续时间|
|**endTime**|String|False| |结束时间|
|**id**|Integer|False| | |
|**jobId**|String|False| | |
|**planId**|String|False| | |
|**startTime**|String|False| |开始时间|
|**status**|String|False| |状态|
|**taskId**|String|False| |作业Id|
|**taskName**|String|False| |作业名称|
|**taskType**|String|False| |作业类型|
|**userpin**|String|False| |用户名|
|**workflowId**|String|False| |工作流Id|
|**workflowInstanceId**|String|False| |工作流实例Id|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|String| |
|**message**|String| |
|**status**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
