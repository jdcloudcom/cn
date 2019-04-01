# stopLiveApp


## 描述
停用 运行中 状态的应用
- 停用应用之后,不能再用此应用名推流


## 请求方式
PUT

## 请求地址
https://live.jdcloud-api.com/v1/apps:stop


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**publishDomain**|String|True| |直播的推流域名|
|**appName**|String|True| |应用名称|


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
https://live.jdcloud-api.com/v1/apps:stop

```
```
{
    "appName": "yourapp", 
    "publishDomain": "push.yourdomain.com"
}
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41"
}
```
