# deleteLiveApp


## 描述
删除应用
- 删除应用之前需要先停用应用
- 删除应用同时会删除此应用下的所有数据


## 请求方式
DELETE

## 请求地址
https://live.jdcloud-api.com/v1/apps/{publishDomain}/appNames/{appName}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**publishDomain**|String|True| |推流域名|
|**appName**|String|True| |应用名称|

## 请求参数
无


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
DELETE
```
https://live.jdcloud-api.com/v1/apps/push.yourdomain.com/appNames/yourapp

```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41"
}
```
