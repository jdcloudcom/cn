# describeBandwidthData


## 描述
带宽统计
- 查询某个时间段内的带宽数据（平均带宽）
- 查询周期：1分钟
- 查询时间跨度：30天


## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/describeStatisticData:bandwidth


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|False| |播放域名，可以通过指定域名查询该域名下产生的带宽数据。<br>|
|**appName**|String|False| |推流AppName，将AppName作为查询条件时须指定域名。<br>|
|**streamName**|String|False| |流名称，将流名称作为查询条件时须指定域名和AppName。<br>|
|**ispName**|String|False| |运营商<br>|
|**locationName**|String|False| |地域<br>|
|**protocolType**|String|False| |协议，取值：HTMP,FLV,HLS<br>|
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
https://live.jdcloud-api.com/v1/describeStatisticData:bandwidth

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
    "result": [
        {
            "data": {}, 
            "endTime": "2019-03-26T07:30:00Z", 
            "startTime": "2019-03-26T07:29:00Z"
        }, 
        {
            "data": {
                "maxValueTime": 1553585460, 
                "value": 25131560
            }, 
            "endTime": "2019-03-26T07:31:00Z", 
            "startTime": "2019-03-26T07:30:00Z"
        }, 
        {
            "data": {
                "maxValueTime": 1553585520, 
                "value": 50263120
            }, 
            "endTime": "2019-03-26T07:32:00Z", 
            "startTime": "2019-03-26T07:31:00Z"
        }
    ]
}
```
