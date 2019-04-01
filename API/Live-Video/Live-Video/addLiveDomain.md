# addLiveDomain


## 描述
添加直播域名
- 创建直播域名之前,必须先开通直播服务
- 直播域名必须已经备案完成


## 请求方式
POST

## 请求地址
https://live.jdcloud-api.com/v1/domains


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**publishDomain**|String|True| |直播的推流域名<br>- 不支持泛域名<br>|
|**playDomain**|String|True| |直播的播放域名<br>- 不支持泛域名<br>|


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
https://live.jdcloud-api.com/v1/domains

```
```
{
    "playDomain": "play.yourdomain.com", 
    "publishDomain": "push.yourdomain.com"
}
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41"
}
```
