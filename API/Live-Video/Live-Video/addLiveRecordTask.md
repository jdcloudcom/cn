# addLiveRecordTask


## 描述
添加打点录制任务
- 您可以调用此接口精确提取已录制的文件中所需要的部分


## 请求方式
POST

## 请求地址
https://live.jdcloud-api.com/v1/records/{publishDomain}/appNames/{appName}/streamNames/{streamName}/task

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**publishDomain**|String|True| |推流域名|
|**appName**|String|True| |应用名称|
|**streamName**|String|True| |流名称|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**recordTimes**|RecordTime[]|True| |录制时间集合 - 最大支持10段,多段合并成一个文件 - 多段时间跨度最小不能小于10s - 多段时间跨度最大不能超过8小时|
|**saveBucket**|String|True| |存储桶|
|**saveEndpoint**|String|True| |存储地址|
|**recordFileType**|String|True| |录制文件类型:<br>- 取值: ts,flv,mp4 (多种类型之前用;隔开)<br>- 不区分大小写<br>|
|**saveObject**|String|False| |录制文件存储路径:<br>- 默认地址: record/{Date}/{ServerId}/{AppName}/{StreamName}/{StartTime}_{EndTime}.{format}<br>|

### RecordTime
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**startTime**|String|True| |开始时间<br>- UTC时间<br>  格式: yyyy-MM-dd'T'HH:mm:ss'Z'<br>  示例: 2018-10-21T10:00:00Z<br>|
|**endTime**|String|True| |结束时间<br>- UTC时间<br>  格式: yyyy-MM-dd'T'HH:mm:ss'Z'<br>  示例: 2018-10-21T10:00:00Z<br>|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|requestId|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|

## 请求示例
POST
```
https://live.jdcloud-api.com/records/push.yourdomain.com/appNames/yourapp/streamNames/yourstream/task

```
```
{
    "appName": "yourapp", 
    "publishDomain": "push.yourdomain.com", 
    "recordFileType": "mp4;flv", 
    "recordTimes": [
        {
            "endTime": "2018-10-21T10:05:00Z", 
            "startTime": "2018-10-21T10:00:00Z"
        }, 
        {
            "endTime": "2018-10-21T10:15:00Z", 
            "startTime": "2018-10-21T10:10:00Z"
        }
    ], 
    "saveBucket": "yourbucket", 
    "saveEndpoint": "oss.xxx.com", 
    "saveObject": "/xxx/xxx/yourobject", 
    "streamName": "yourstream"
}
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41"
}
```
