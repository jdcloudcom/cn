# describePublishStreamInfoData


## 描述
查询推流监控数据

## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/describePublishStreamInfoData


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|True| |推流域名|
|**appName**|String|True| |应用名称|
|**streamName**|String|True| |流名称|
|**startTime**|String|True| |起始时间<br>- UTC时间<br>  格式:yyyy-MM-dd'T'HH:mm:ss'Z'<br>  示例:2018-10-21T10:00:00Z<br>|
|**endTime**|String|False| |结束时间:<br>- UTC时间<br>  格式:yyyy-MM-dd'T'HH:mm:ss'Z'<br>  示例:2018-10-21T10:00:00Z<br>- 为空,默认为当前时间，查询时间跨度不超过1天<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|requestId|

### Result
|名称|类型|描述|
|---|---|---|
|**dataList**|PublishStreamInfoResult[]| |
### PublishStreamInfoResult
|名称|类型|描述|
|---|---|---|
|**startTime**|String|起始时间点，UTC时间，格式：yyyy-MM-dd'T'HH:mm:ss'Z'<br>|
|**endTime**|String|结束时间点，UTC时间，格式：yyyy-MM-dd'T'HH:mm:ss'Z'<br>|
|**data**|PublishStreamInfoData| |
### PublishStreamInfoData
|名称|类型|描述|
|---|---|---|
|**streamName**|String|流名称<br>|
|**fps**|String|帧率<br>|
|**bitrate**|String|码率，单位：bps<br>|
|**pushEdgeNodeIps**|String[]|CDN上行节点IP列表<br>|
|**anchorIps**|String[]|主播IP列表<br>|
|**flvBandWidth**|Long|Flv观看带宽<br>|
|**flvPlayerCount**|Long|Flv观看人数<br>|
|**hlsBandWidth**|Long|Hls观看带宽<br>|
|**hlsPlayerCount**|Long|Hls观看人数<br>|

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
https://live.jdcloud-api.com/v1/describePublishStreamInfoData?domainName=yourdomain&appName=yourapp&streamName=yourstream&startTime=2018-10-21T10:00:00Z&&endTime=2018-10-22T10:00:00Z
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "dataList": [
            {
                "data": {
                    "anchorIps": [
                        "12.10.10.11", 
                        "12.10.10.12"
                    ], 
                    "bitrate": "700100", 
                    "flvBandWidth": "", 
                    "flvPlayerCount": "", 
                    "fps": "25.0", 
                    "hlsBandWidth": "", 
                    "hlsPlayerCount": "", 
                    "pushEdgeNodeIps": [
                        "121.123.123.123", 
                        "121.123.123.124"
                    ]
                }, 
                "endTime": "2018-10-21T10:01:00Z", 
                "startTime": "2018-10-21T10:00:00Z"
            }, 
            {
                "data": {
                    "anchorIps": [
                        "12.10.10.11", 
                        "12.10.10.12"
                    ], 
                    "bitrate": "700200", 
                    "flvBandWidth": "", 
                    "flvPlayerCount": "", 
                    "fps": "25.0", 
                    "hlsBandWidth": "", 
                    "hlsPlayerCount": "", 
                    "pushEdgeNodeIps": [
                        "121.123.123.123", 
                        "121.123.123.124"
                    ]
                }, 
                "endTime": "2018-10-21T10:02:00Z", 
                "startTime": "2018-10-21T10:01:00Z"
            }
        ]
    }
}
```
