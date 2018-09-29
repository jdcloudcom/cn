# modifyJob


## 描述
按照传入的参数信息修改对应作业信息

## 请求方式
POST

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/job:modify

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**jmrJobViewModel**|JmrJobViewModel|True| |需要传入clusterId、jobName、jobType、location、jobArgs、retryTimes、isSendMsg|

### JmrJobViewModel
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clusterId**|String|False| |集群ID|
|**clusterName**|String|False| |集群名称|
|**clusterStatus**|String|False| |额外字段|
|**createTime**|String|False| |创建时间|
|**cronExpression**|String|False| |定时任务的时间|
|**dataCenter**|String|False| |数据中心|
|**id**|Integer|False| | |
|**isSelfDependence**|Integer|False| | |
|**isSendMsg**|Boolean|False| |作业失败后是否发送短信通知|
|**isVirtualTask**|Integer|False| | |
|**jobGroup**|String|False| |作业组|
|**jobId**|String|False| |作业ID|
|**jobName**|String|False| |作业名称|
|**jobStatus**|String|False| |作业状态|
|**jobTrigger**|String|False| |作业触发器|
|**jobType**|String|False| |作业类型|
|**location**|String|False| |位置|
|**orderBy**|String|False| |额外字段，可选|
|**params**|String|False| |所需参数|
|**retryTimes**|Integer|False| |作业重试次数|
|**taskScheduleType**|Integer|False| | |
|**userpin**|String|False| |用户名|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**message**|String| |
|**status**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
