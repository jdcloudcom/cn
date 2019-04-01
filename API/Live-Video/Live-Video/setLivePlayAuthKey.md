# setLivePlayAuthKey


## 描述
设置播放鉴权KEY

## 请求方式
POST

## 请求地址
https://live.jdcloud-api.com/v1/livePlayAuthKey


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**playDomain**|String|True| |播放域名|
|**authStatus**|String|False| |播放鉴权状态<br>  on: 开启<br>  off: 关闭<br>- 当推流鉴权状态on(开启)时,authKey不能为空<br>|
|**authKey**|String|False| |播放鉴权key<br>- 取值: 支持大小写字母和数字 长度6-32位<br>|


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
https://live.jdcloud-api.com/v1/setLivePlayAuthKey

```
```
{
    "authKey": "testAuthKey123", 
    "authStatus": "on", 
    "playDomain": "play.yourdomain.com"
}
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41"
}
```
