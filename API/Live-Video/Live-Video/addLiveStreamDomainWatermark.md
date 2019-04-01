# addLiveStreamDomainWatermark


## 描述
添加域名水印配置


## 请求方式
POST

## 请求地址
https://live.jdcloud-api.com/v1/watermarkDomains:config


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**publishDomain**|String|True| |推流域名|
|**template**|String|True| |水印模板<br>|


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
https://live.jdcloud-api.com/v1/watermarkDomains:config

```
```
{
    "publishDomain": "push.yourdomain.com", 
    "template": "yourwatermarktemplate"
}
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41"
}
```
