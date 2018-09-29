# getCronJobList


## 描述
获取执行计划列表

## 请求方式
POST

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/cronJob:list

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**jmrPlanViewModel**|JmrPlanViewModel|True| |需要传入的字段： az、planName、planType、planStatus|
|**selectParams**|SelectParams|False| |搜索条件的可选参数|

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
### SelectParams
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**orderBy**|String|False| |排序条件，可选|
|**pageNum**|Integer|False| |搜索分页页数，可选条件|
|**pageSize**|Integer|False| |搜索分页大小，可选条件|
|**status**|String|False| | |

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|Object|"包括JmrPlanViewModel列表 - cronJobs"<br>"以及返回列表大小 - totalNum"<br>|
|**message**|String| |
|**status**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
