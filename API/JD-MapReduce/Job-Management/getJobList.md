# getJobList


## 描述
获取指定集群下的作业列表

## 请求方式
POST

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/jobView:list

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**jmrJobViewModel**|JmrJobViewModel|True| |"需要传入字段: clusterId、az"<br>"可选字段: jobName、jobType、clusterName"<br>|
|**selectParams**|SelectParams|False| | |

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
|**data**|Object|"包括JmrJobViewModel列表 - jmrJobViewModelList"<br>"以及返回的列表大小 - totalNum"<br>|
|**message**|String| |
|**status**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
