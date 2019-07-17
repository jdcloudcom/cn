# addLiveStreamDomainSnapshot


## 描述
添加域名截图配置
- 添加域名级别的截图模板配置


## 请求方式
POST

## 请求地址
https://live.jdcloud-api.com/v1/snapshotDomains:template


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**publishDomain**|String|True| |推流域名|
|**template**|String|True| |截图模板|


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
https://live.jdcloud-api.com/v1/snapshotDomains:template
```

```
{
    "publishDomain": "push.yourdomain.com", 
    "template": "yoursnapshottemplate"
}
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41"
}
```
