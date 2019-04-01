# describeTranscodingDurationData


## 描述
转码时长统计

## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/describeStatisticData:transcode


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|False| |推流域名，可以通过指定域名查询该域名下产生的转码时长数据。<br>|
|**appName**|String|False| |推流AppName，将AppName作为查询条件时须指定域名。<br>|
|**streamName**|String|False| |流名称，将流名称作为查询条件时须指定域名和AppName。<br>|
|**grade**|String|False| |码率档次，取值与转码模板中的档次对应，可以查询指定档次的转码时长。<br>|
|**startTime**|String|True| |查询起始时间，UTC时间，格式：yyyy-MM-dd'T'HH:mm:ss'Z'<br>|
|**endTime**|String|True| |查询截至时间，UTC时间，格式：yyyy-MM-dd'T'HH:mm:ss'Z'<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Array|统计结果|
|**requestId**|String|ruquestId|


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
GET
```
https://live.jdcloud-api.com/v1/describeStatisticData:transcode

```
```
{
    "endTime": "2019-03-25T16:00:00Z", 
    "startTime": "2019-03-24T16:00:00Z"
}
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": [
        {
            "date": "2019-03-24T16:00:00Z", 
            "duration": 1066815
        }
    ]
}
```
