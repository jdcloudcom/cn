# describeLivePublishStreamNum


## 描述
查询直播推流数

## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/describeLivePublishStreamNum


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|False| |播放域名|
|**appName**|String|False| |应用名称|
|**protocolType**|String|False| |查询的流协议类型，取值范围："rtmp,hdl,hls"，多个时以逗号分隔<br>|
|**ispName**|String|False| |[运营商](../Reference/Operator.md)<br>|
|**locationName**|String|False| |[地域](../Reference/Region.md)，如beijing,shanghai。多个用逗号分隔<br>|
|**period**|String|False| |查询周期，当前取值范围：“oneMin,fiveMin,halfHour,hour,twoHour,sixHour,day,followTime”，分别表示1min，5min，半小时，1小时，2小时，6小时，1天，跟随时间。默认为空，表示fiveMin。当传入followTime时，表示按Endtime-StartTime的周期，只返回一个点<br>|
|**startTime**|String|True| |起始时间<br>- UTC时间<br>  格式:yyyy-MM-dd'T'HH:mm:ss'Z'<br>  示例:2018-10-21T10:00:00Z<br>|
|**endTime**|String|False| |结束时间:<br>- UTC时间<br>  格式:yyyy-MM-dd'T'HH:mm:ss'Z'<br>  示例:2018-10-21T10:00:00Z<br>- 为空,默认为当前时间<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|requestId|

### Result
|名称|类型|描述|
|---|---|---|
|**dataList**|LiveStreamUserNumResult[]| |
### LiveStreamUserNumResult
|名称|类型|描述|
|---|---|---|
|**startTime**|String|起始时间点，UTC时间，格式：yyyy-MM-dd'T'HH:mm:ss'Z'<br>|
|**endTime**|String|结束时间点，UTC时间，格式：yyyy-MM-dd'T'HH:mm:ss'Z'<br>|
|**data**|LiveStreamUserNumResultData| |
### LiveStreamUserNumResultData
|名称|类型|描述|
|---|---|---|
|**count**|Long|人数<br>|

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
https://live.jdcloud-api.com/v1/describeLivePublishStreamNum?domainName=push.yourdomain.com&appName=yourapp&startTime=2018-10-21T10:00:00Z&&endTime=2018-10-22T10:00:00Z
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "dataList": [
            {
                "data": {
                    "count": 23
                }, 
                "endTime": "2018-10-21T10:01:00Z", 
                "startTime": "2018-10-21T10:00:00Z"
            }, 
            {
                "data": {
                    "count": 30
                }, 
                "endTime": "2018-10-21T10:02:00Z", 
                "startTime": "2018-10-21T10:01:00Z"
            }
        ]
    }
}
```
