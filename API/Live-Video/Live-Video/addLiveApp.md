# addLiveApp


## 描述
添加直播应用名
- 需要提前在应用(app)级别绑定功能模板时才需要提前新建应用名
- 新的应用名可以推流时自动创建


## 请求方式
POST

## 请求地址
https://live.jdcloud-api.com/v1/apps


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**publishDomain**|String|True| |直播的推流域名|
|**appName**|String|True| |应用名称<br>- 取值: 数字字母中划线("-")下划线("_") 50个字符以内<br>|


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
https://live.jdcloud-api.com/v1/apps

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
