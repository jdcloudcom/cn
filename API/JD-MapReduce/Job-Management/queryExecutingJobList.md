# queryExecutingJobList


## 描述
获取计划中的任务(已经添加到quartz调度器的任务)

## 请求方式
GET

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/executingJob:list

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
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
|**data**|JmrPlanViewModel[]|执行计划列表|
|**message**|String| |
|**status**|String| |
### JmrPlanViewModel
|名称|类型|描述|
|---|---|---|
|**az**|String| |
|**clusterId**|String| |
|**clusterName**|String| |
|**createTime**|String|创建时间|
|**cronExpression**|String|formatt后的时间|
|**dataCenter**|String|数据中心，即regionId|
|**description**|String| |
|**failurePolicy**|String|任务调度失败时采用的策略|
|**isSync**|Boolean| |
|**jobGroup**|String| |
|**jobIds**|String| |
|**jobTrigger**|String|触发器|
|**modifyTime**|String|修改时间|
|**orderBy**|String| |
|**planId**|Number|任务调度id|
|**planName**|String| |
|**planStatus**|String| |
|**planType**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
