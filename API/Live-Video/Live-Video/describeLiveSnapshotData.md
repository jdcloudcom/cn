# describeLiveSnapshotData


## 描述
查询直播截图张数数据

## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/liveSnapshotData


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**publishDomain**|String|True| |推流域名|
|**appName**|String|False| |应用名称|
|**streamName**|String|False| |流名称|
|**startTime**|String|True| |起始时间:<br>- UTC时间<br>  格式: yyyy-MM-dd'T'HH:mm:ss'Z'<br>  示例: 2018-10-21T10:00:00Z<br>- 支持最大查询90天以内的数据<br>|
|**endTime**|String|False| |结束时间:<br>- UTC时间<br>  格式: yyyy-MM-dd'T'HH:mm:ss'Z'<br>  示例: 2018-10-21T10:00:00Z<br>- 为空,默认当前时间<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|requestId|

### Result
|名称|类型|描述|
|---|---|---|
|**snapshotData**|SnapshotData[]| |
### SnapshotData
|名称|类型|描述|
|---|---|---|
|**publishDomain**|String|推流域名|
|**appName**|String|应用名称|
|**streamName**|String|流名称|
|**date**|String|日期<br>- 格式: yyyyMMdd<br>- 示例: 20190308<br>|
|**total**|Integer|截图张数<br>- 单位: 张<br>|

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
https://live.jdcloud-api.com/v1/liveSnapshotData?publishDomain=push.yourdomain.com&appName=yourapp&streamName=yourstream&startTime=2018-10-21T10:00:00Z

```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "snapshotDatas": [
            {
                "appName": "yourapp", 
                "date": "20180101", 
                "publishDomain": "push.yourdomain.com", 
                "streamName": "yourstream", 
                "total": 86310
            }, 
            {
                "appName": "yourapp", 
                "date": "20180102", 
                "publishDomain": "push.yourdomain.com", 
                "streamName": "yourstream", 
                "total": 86310
            }
        ]
    }
}
```
