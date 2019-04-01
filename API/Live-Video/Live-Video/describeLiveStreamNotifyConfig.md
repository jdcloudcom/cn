# describeLiveStreamNotifyConfig


## 描述
查询直播流状态回调地址

## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/streamNotifys/{publishDomain}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**publishDomain**|String|True| |推流域名|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|requestId|

### Result
|名称|类型|描述|
|---|---|---|
|**publishDomain**|String|推流域名|
|**notifyUrl**|String|流状态回调地址|

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
https://live.jdcloud-api.com/v1/streamNotifys/push.yourdomain.com

```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "notifyUrl": "http://xxx.com/xxx/xxx", 
        "publishDoamin": "push.yourdomain.com"
    }
}
```
