# describeUrlRanking


## 描述
查询URL播放排行

## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/describeUrlRanking


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|True| |播放域名|
|**size**|Integer|False| |查询Top数量，默认20，即返回Top20的数据|
|**rankfield**|String|False| |排行依据字段，取值：["pv", "flow", "bandwidth"]，默认pv<br>- pv 播放次数<br>- flow 流量<br>- bandwidth 带宽<br>|
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
|**dataList**|RankingUrlResult[]| |
### RankingUrlResult
|名称|类型|描述|
|---|---|---|
|**rankingList**|RankingUrlResultData[]| |
### RankingUrlResultData
|名称|类型|描述|
|---|---|---|
|**url**|String|URL<br>|
|**rank**|Integer|排行序号<br>|
|**md5**|String|文件md5<br>|
|**value**|Long|排行依据字段对应的数值<br>|
|**data**|RankingUrlResultRankData[]| |
### RankingUrlResultRankData
|名称|类型|描述|
|---|---|---|
|**uv**|Long|独立访问数<br>|
|**bandwidth**|Long|带宽，单位：bps<br>|
|**pv**|Long|访问次数<br>|
|**flow**|Long|流量，单位：Byte|

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
https://live.jdcloud-api.com/v1/describeUrlRanking?domains=play.yourdomain.com&startTime=2018-10-21T10:00:00Z
```

## 返回示例
```
{
    "code": 200, 
    "requestId": "bkcu3ts60jt1f86ti756imamqaw18puj", 
    "result": {
        "rankingList": [
            {
                "data": {
                    "bandwidth": 1324, 
                    "flow": 59344, 
                    "pv": 118, 
                    "uv": 7
                }, 
                "rank": 1, 
                "url": "pl.jdcloud.com/ccc/copy.m3u8", 
                "value": 118
            }
        ]
    }
}
```
