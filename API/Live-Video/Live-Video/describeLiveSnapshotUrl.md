# describeLiveSnapshotUrl


## 描述
获取截图地址


## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/snapshots/{imgId}:url


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**imgId**|String|True| |截图ID<br>|
|**authExpire**|Integer|False| |地址有效期，单位：秒，默认：3600<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|requestId|

### Result
|名称|类型|描述|
|---|---|---|
|**imgId**|String|截图ID|
|**imgUrl**|String|图片地址|

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
https://live.jdcloud-api.com/v1/snapshots/{imgId}:url
```

```
{
    "authExpire": 3600
}
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "imgId": "", 
        "imgUrl": ""
    }
}
```
