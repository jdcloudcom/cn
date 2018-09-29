# showJobDetails


## 描述
查看指定jobId对应的作业明细

## 请求方式
POST

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/{jobId}:detail

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**jobId**|String|True| |需要查看的作业的Id|
|**regionId**|String|True| |地域ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|JmrJobViewModel| |
|**message**|String| |
|**status**|String| |
### JmrJobViewModel
|名称|类型|描述|
|---|---|---|
|**clusterId**|String|集群ID|
|**clusterName**|String|集群名称|
|**clusterStatus**|String|额外字段|
|**createTime**|String|创建时间|
|**cronExpression**|String|定时任务的时间|
|**dataCenter**|String|数据中心|
|**id**|Integer| |
|**isSelfDependence**|Integer| |
|**isSendMsg**|Boolean|作业失败后是否发送短信通知|
|**isVirtualTask**|Integer| |
|**jobGroup**|String|作业组|
|**jobId**|String|作业ID|
|**jobName**|String|作业名称|
|**jobStatus**|String|作业状态|
|**jobTrigger**|String|作业触发器|
|**jobType**|String|作业类型|
|**location**|String|位置|
|**orderBy**|String|额外字段，可选|
|**params**|String|所需参数|
|**retryTimes**|Integer|作业重试次数|
|**taskScheduleType**|Integer| |
|**userpin**|String|用户名|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
