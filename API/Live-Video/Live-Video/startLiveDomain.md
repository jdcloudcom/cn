# startLiveDomain


## 描述
启动域名
- 启用状态为 停用 的直播域名对(推流域名,播放域名)将DomainStatus变更为online


## 请求方式
PUT

## 请求地址
https://live.jdcloud-api.com/v1/domains:start


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**publishDomain**|String|True| |推流域名<br>- 需要启动的域名对(推流域名,播放域名)中的推流域名<br>|


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
https://live.jdcloud-api.com/v1/domains:start

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
