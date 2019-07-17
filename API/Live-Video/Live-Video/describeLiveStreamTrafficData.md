# describeLiveStreamTrafficData


## 描述
查询流量数据
- 查询某个时间段内的流量数据。
- 查询1分钟粒度的数据时，时间跨度不超过7天，其他粒度时时间跨度不超过30天


## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/describeLiveStreamTrafficData


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|False| |播放域名，可以通过指定域名查询该域名下产生的带宽数据。<br>|
|**appName**|String|False| |推流AppName，将AppName作为查询条件时须指定域名。<br>|
|**streamName**|String|False| |流名称<br>|
|**ispName**|String|False| |[运营商](../Reference/Operator.md)<br>|
|**locationName**|String|False| |[地域](../Reference/Region.md)，如beijing,shanghai。多个用逗号分隔<br>|
|**protocolType**|String|False| |查询的流协议类型，取值范围："rtmp,hdl,hls"，多个时以逗号分隔<br>|
|**period**|String|False| |查询周期，当前取值范围：“oneMin,fiveMin,halfHour,hour,twoHour,sixHour,day,followTime”，分别表示1min，5min，半小时，1小时，2小时，6小时，1天，跟随时间。默认为空，表示fiveMin。当传入followTime时，表示按Endtime-StartTime的周期，只返回一个点<br>|
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
|**dataList**|TrafficStatisticResult[]| |
### TrafficStatisticResult
|名称|类型|描述|
|---|---|---|
|**startTime**|String|时间点<br>|
|**endTime**|String|时间点<br>|
|**data**|TrafficStatisticResultData| |
### TrafficStatisticResultData
|名称|类型|描述|
|---|---|---|
|**value**|Long|流量，单位:Byte<br>|

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
https://live.jdcloud-api.com/v1/describeLiveStreamTrafficData?domainName=xxx
```

```
{
    "endTime": "2019-03-27T16:00:00Z", 
    "startTime": "2019-03-26T16:00:00Z"
}
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "dataList": [
            {
                "data": {
                    "value": 188486700
                }, 
                "endTime": "2019-03-26T07:31:00Z", 
                "startTime": "2019-03-26T07:30:00Z"
            }, 
            {
                "data": {
                    "value": 376973400
                }, 
                "endTime": "2019-03-26T07:32:00Z", 
                "startTime": "2019-03-26T07:31:00Z"
            }, 
            {
                "data": {
                    "value": 376973400
                }, 
                "endTime": "2019-03-26T07:33:00Z", 
                "startTime": "2019-03-26T07:32:00Z"
            }
        ]
    }
}
```
