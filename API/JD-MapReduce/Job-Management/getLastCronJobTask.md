# getLastCronJobTask


## 描述
获取定时任务的某个作业的最后一次运行记录

## 请求方式
POST

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/lastCronJobTask/{jobId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**jobId**|String|True| |作业ID|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**planId**|String|True| |定时任务ID，必传|


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
