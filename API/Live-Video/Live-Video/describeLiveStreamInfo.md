# describeLiveStreamInfo


## 描述
查询直播实时流信息


## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/streams/{publishDomain}/appNames/{appName}/streamNames/{streamName}/streamInfo

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**publishDomain**|String|True| |推流域名|
|**appName**|String|True| |应用名称|
|**streamName**|String|True| |流名称|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|ruquestId|

### Result
|名称|类型|描述|
|---|---|---|
|**publishDomain**|String|推流域名|
|**appName**|String|应用名称|
|**streamName**|String|流名称|
|**status**|String|流状态<br>  on: 在线流<br>  off: 非在线流<br>|

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
https://live.jdcloud-api.com/v1/streams/push.yourdomain.com/appNames/yourapp/streamNames/yourstream/streamInfo

```

## 返回示例
```
{
    "RequestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "appName": "yourapp", 
        "publishDomain": "push.yourdomain.com", 
        "status": "on", 
        "streamName": "yourstream"
    }
}
```
