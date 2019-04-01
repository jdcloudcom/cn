# stopLiveDomain


## 描述
停用域名
- 停用直播域名对(推流域名,播放域名),将DomainStatus变更为offline
- 停用该直播域名对后,直播域名信息仍保留,但用户将不能再用该推流域名推流或播放域名播放


## 请求方式
PUT

## 请求地址
https://live.jdcloud-api.com/v1/domains:stop


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**publishDomain**|String|True| |推流域名<br>- 需要停用的域名对(推流域名,播放域名)中的推流域名<br>|


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
https://live.jdcloud-api.com/v1/domains:stop

```
```
{
    "publishDomain": "push.yourdomain.com"
}
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41"
}
```
