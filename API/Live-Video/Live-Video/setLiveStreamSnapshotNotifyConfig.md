# setLiveStreamSnapshotNotifyConfig


## 描述
设置直播截图回调通知地址


## 请求方式
POST

## 请求地址
https://live.jdcloud-api.com/v1/snapshotNotifys:config


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**publishDomain**|String|True| |推流域名|
|**notifyUrl**|String|True| |截图回调通知的URL地址:<br>- 以 http:// 开头,外网可访问的地址<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|requestId|


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
POST
```
https://live.jdcloud-api.com/v1/snapshotNotifys:config

```
```
{
    "notifyUrl": "http://xxx.com/xxx/xxx", 
    "publishDomain": "push.yourdomain.com"
}
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41"
}
```
