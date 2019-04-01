# addLiveRestartDomain


## 描述
添加回看域名


## 请求方式
PUT

## 请求地址
https://live.jdcloud-api.com/v1/domains:restart


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**playDomain**|String|True| |直播的播放域名<br>- 回看域名所对应的原播放域名,新建的回看域名将绑定到此播放域名下<br>|
|**restartDomain**|String|True| |直播回看域名<br>- 直播域名必须已经备案完成<br>|


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
PUT
```
https://live.jdcloud-api.com/v1/domains:restart

```
```
{
    "playDomain": "play.yourdomain.com", 
    "restartDomain": "restart.yourdomain.com"
}
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41"
}
```
