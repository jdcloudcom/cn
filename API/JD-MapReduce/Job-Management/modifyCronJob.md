# modifyCronJob


## 描述
修改部署作业的执行计划

## 请求方式
POST

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/cronJob:modify

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**day**|String|True| |按照Cron格式的时间参数,占位day|
|**hour**|String|True| |按照Cron格式的时间参数,占位hour|
|**jmrPlanViewModel**|JmrPlanViewModel|True| |"需要传入字段: planId、jobIds、planName、planType、failurePolicy"<br>|
|**minute**|String|True| |按照Cron格式的时间参数,占位minute|
|**month**|String|True| |按照Cron格式的时间参数,占位month|
|**time**|String|True| |按照Cron格式的时间参数,占位time|
|**week**|String|True| |按照Cron格式的时间参数,占位week|

### JmrPlanViewModel
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**az**|String|False| | |
|**clusterId**|String|False| | |
|**clusterName**|String|False| | |
|**createTime**|String|False| |创建时间|
|**cronExpression**|String|False| |formatt后的时间|
|**dataCenter**|String|False| |数据中心，即regionId|
|**description**|String|False| | |
|**failurePolicy**|String|False| |任务调度失败时采用的策略|
|**isSync**|Boolean|False| | |
|**jobGroup**|String|False| | |
|**jobIds**|String|False| | |
|**jobTrigger**|String|False| |触发器|
|**modifyTime**|String|False| |修改时间|
|**orderBy**|String|False| | |
|**planId**|Number|False| |任务调度id|
|**planName**|String|False| | |
|**planStatus**|String|False| | |
|**planType**|String|False| | |

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
