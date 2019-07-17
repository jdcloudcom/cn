# describeLiveTranscodingDurationData


## 描述
查询转码时长数据

## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/describeLiveTranscodingDurationData


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**grade**|String|False| |码率档次，可以查询指定档次的转码时长，取值：<br>- video_h264_4k_1<br>- video_h264_2k_1<br>- video_h264_shd_1<br>- video_h264_hd_1<br>- video_h264_sd_1<br>- video_h265_4k_1<br>- video_h265_2k_1<br>- video_h265_shd_1<br>- video_h265_hd_1<br>- video_h265_sd_1<br>|
|**period**|String|False| |查询周期，取值范围：“day,month,year,followTime”，分别表示1天，1月，1年，跟随时间。默认为空，表示day。当传入followTime时，表示按Endtime-StartTime的周期，只返回一个点<br>|
|**startTime**|String|True| |查询起始时间，UTC时间，格式：yyyy-MM-dd'T'HH:mm:ss'Z'<br>|
|**endTime**|String|False| |查询截至时间，UTC时间，格式：yyyy-MM-dd'T'HH:mm:ss'Z'，为空时默认为当前时间<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|ruquestId|

### Result
|名称|类型|描述|
|---|---|---|
|**dataList**|TranscodeDurationStatisticResult[]| |
### TranscodeDurationStatisticResult
|名称|类型|描述|
|---|---|---|
|**startTime**|String|时间点<br>|
|**endTime**|String|时间点<br>|
|**data**|TranscodeDurationStatisticData| |
### TranscodeDurationStatisticData
|名称|类型|描述|
|---|---|---|
|**duration**|String|时长，单位：秒<br>|

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
https://live.jdcloud-api.com/v1/describeLiveTranscodingDurationData?startTime=2018-10-21T16:00:00Z&endTime=2019-03-25T16:00:00Z
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "dataList": [
            {
                "data": {
                    "duration": 39964780
                }, 
                "endTime": "2019-03-28T15:59:59Z", 
                "startTime": "2019-03-27T16:00:00Z"
            }, 
            {
                "data": {
                    "duration": 26255406
                }, 
                "endTime": "2019-03-26T15:59:59Z", 
                "startTime": "2019-03-25T16:00:00Z"
            }
        ]
    }
}
```
