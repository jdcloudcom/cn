# describeLiveDomainDetail


## 描述
查询指定域名相关信息

## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/domains/{publishDomain}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**publishDomain**|String|True| |推流域名
- 需要停用的域名对(推流域名,播放域名)中的推流域名
|

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
|**publishDomains**|PublishDomain[]|推流域名集合|
|**playDomains**|PlayDomain[]|直播域名集合|
### PlayDomain
|名称|类型|描述|
|---|---|---|
|**playDomain**|String|播放域名|
|**playDomainCname**|String|播放域名Cname|
|**domainStatus**|String|直播域名状态<br>  online: 启用<br>  offline: 停用<br>  configuring: 配置中<br>  configure_failed: 配置失败<br>  checking: 正在审核<br>  check_failed: 审核失败<br>|
|**playType**|String|播放域名类型<br>  normal: 普通播放域名<br>  restart: 回看域名<br>|
|**createTime**|String|域名创建时间<br>- UTC时间<br>  格式: yyyy-MM-dd'T'HH:mm:ss'Z'<br>|
|**updateTime**|String|域名更新时间<br>- UTC时间<br>  格式: yyyy-MM-dd'T'HH:mm:ss'Z'<br>|
### PublishDomain
|名称|类型|描述|
|---|---|---|
|**publishDomain**|String|推流域名|
|**publishDomainCname**|String|推流域名Cname|
|**domainStatus**|String|直播域名状态<br>  online: 启用<br>  offline: 停用<br>  configuring: 配置中<br>  configure_failed: 配置失败<br>  checking: 正在审核<br>  check_failed: 审核失败<br>|
|**createTime**|String|域名创建时间<br>- UTC时间<br>  格式: yyyy-MM-dd'T'HH:mm:ss'Z'<br>|
|**updateTime**|String|域名更新时间<br>- UTC时间<br>  格式: yyyy-MM-dd'T'HH:mm:ss'Z'<br>|

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
https://live.jdcloud-api.com/v1/domains/push.yourdomain.com

```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "playDomain": [
            {
                "createTime": "2017-11-27T06:51:25Z", 
                "domainStatus": "online", 
                "playDomain": "play.yourdomain.com", 
                "playType": "normal", 
                "publishDomainCname": "play.yourdomain.com.live-play.xxx.jcloud-cdn.com", 
                "updateTime": "2017-11-27T06:51:26Z"
            }
        ], 
        "publishDomain": [
            {
                "createTime": "2017-11-27T06:51:25Z", 
                "domainStatus": "online", 
                "publishDomain": "push.yourdomain.com", 
                "publishDomainCname": "push.yourdomain.com.live-publish.xxx.jcloud-cdn.com", 
                "updateTime": "2017-11-27T06:51:26Z"
            }
        ]
    }
}
```
