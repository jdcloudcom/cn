# describeLiveDomains


## 描述
查询域名列表

## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/domains


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNum**|Integer|False|1|页码<br>- 取值范围[1, 100000]<br>|
|**pageSize**|Integer|False|10|分页大小<br>- 取值范围[10, 100]<br>|
|**publishDomain**|String|False| |推流域名<br>- 目前仅支持精确查询<br>- 为空时,查询用户所有直播域名<br>|


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
|**domainDetails**|DomainDetails[]|域名信息集合|
### DomainDetails
|名称|类型|描述|
|---|---|---|
|**publishDomains**|PublishDomain[]|推流域名集合|
|**playDomains**|PlayDomain[]|播放域名集合|
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
https://live.jdcloud-api.com/v1/domains?publishDomain=push.yourdomain.com

```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "domainDetails": [
            {
                "playDomains": [
                    {
                        "createTime": "2017-11-27T06:51:25Z", 
                        "playDomain": "play.yourdomain.com", 
                        "playDomainCname": "play.yourdomain.com.live-play.xxx.jcloud-cdn.com", 
                        "playDomainStatus": "online", 
                        "playType": "normal", 
                        "updateTime": "2017-11-27T06:51:26Z"
                    }
                ], 
                "publishDomains": [
                    {
                        "createTime": "2017-11-27T06:51:25Z", 
                        "publishDomain": "push.yourdomain.com", 
                        "publishDomainCname": "push.yourdomain.com.live-publish.xxx.jcloud-cdn.com", 
                        "publishDomainStatus": "online", 
                        "updateTime": "2017-11-27T06:51:26Z"
                    }
                ]
            }
        ], 
        "pageNumber": 1, 
        "pageSize": 10, 
        "totalCount": 1
    }
}
```
