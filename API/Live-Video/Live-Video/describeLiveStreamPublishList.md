# describeLiveStreamPublishList


## 描述
查看推流历史记录

## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/streams/{publishDomain}/publishList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**publishDomain**|String|True| |推流域名|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNum**|Integer|False|1|页码<br><br>- 取值范围[1, 100000]<br>|
|**pageSize**|Integer|False|10|分页大小<br><br>- 取值范围[10, 100]<br>|
|**appName**|String|False| |应用名称|
|**streamName**|String|False| |流名称|
|**startTime**|String|True| |推流起始时间<br><br>- UTC时间<br>  格式:yyyy-MM-dd'T'HH:mm:ss'Z'<br>  示例:2018-10-21T10:00:00Z<br>- 最大支持最近90天内的流历史查询<br>|
|**endTime**|String|False|当前时间|推流结束时间<br><br>- UTC时间<br>  格式:yyyy-MM-dd'T'HH:mm:ss'Z'<br>  示例:2018-10-21T10:00:00Z<br>- 最大支持最近90天内的流历史查询<br>- 结束时间为空默认为当前时间<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|requestId|

### Result
|名称|类型|描述|
|---|---|---|
|**pageNumber**|Integer|当前页码|
|**pageSize**|Integer|每页数量|
|**totalCount**|Integer|查询总数|
|**liveStreamPublishInfos**|LiveStreamPublishInfo[]|推流历史集合|
### LiveStreamPublishInfo
|名称|类型|描述|
|---|---|---|
|**publishDomain**|String|推流域名|
|**appName**|String|应用名称|
|**streamName**|String|流名称|
|**publishUpTime**|String|推流开始时间<br>- UTC时间<br>  格式:yyyy-MM-dd'T'HH:mm:ss'Z'<br>|
|**publishDownTime**|String|推流结束时刻<br>- UTC时间<br>  格式:yyyy-MM-dd'T'HH:mm:ss'Z'<br>|

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
https://live.jdcloud-api.com/v1/streams/push.yourdomain.com/onlineList?appName=yourapp&streamName=yourstream&startTime=2015-12-02T01:00:00Z&endTime=2015-12-02T04:00:00Z

```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "liveStreamPublishInfos": [
            {
                "appName": "yourapp", 
                "publishDomain": "push.yourdomain.com", 
                "publishDownTime": "2015-12-02T03:11:19Z", 
                "publishUpTime": "2015-12-02T03:05:53Z", 
                "streamName": "yourstream"
            }
        ], 
        "pageNumber": 1, 
        "pageSize": 10, 
        "totalCount": 1
    }
}
```
