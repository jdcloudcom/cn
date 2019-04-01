# describeLiveTimeshiftConfigs


## 描述
查询时移配置

## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/liveTimeshift:configs


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False|1|页码<br>- 取值范围[1, 100000]<br>|
|**pageSize**|Integer|False|10|分页大小<br>- 取值范围[10, 100]<br>|
|**playDomain**|String|True| |直播的播放域名<br>- 目前仅支持精确匹配<br>|


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
|**timeshiftConfigs**|TimeshiftConfig[]|直播域名集合|
### TimeshiftConfig
|名称|类型|描述|
|---|---|---|
|**publishDomains**|TimeshiftPublishDomain[]|推流域名集合|
|**playDomains**|TimeshiftPlayDomain[]|播放域名集合|
### TimeshiftPlayDomain
|名称|类型|描述|
|---|---|---|
|**playDomain**|String|播放域名|
|**timeshiftStatus**|String|直播时移状态:<br>  on: 开启<br>  off: 关闭<br>|
|**playType**|String|播放域名类型:<br>  normal: 普通播放域名(时移播放域名)<br>|
### TimeshiftPublishDomain
|名称|类型|描述|
|---|---|---|
|**publishDomain**|String|推流域名|

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
https://live.jdcloud-api.com/v1/liveTimeshift:configs?playDomain=play.yourdomain.com

```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "pageNumber": 1, 
        "pageSize": 10, 
        "timeshiftConfigs": [
            {
                "playDomains": [
                    {
                        "playDomain": "play.yourdomain.com", 
                        "playType": "normal", 
                        "timeshiftStatus": "on"
                    }
                ], 
                "publishDomains": [
                    {
                        "publishDomain": "push.yourdomain.com"
                    }
                ]
            }
        ], 
        "totalCount": 1
    }
}
```
