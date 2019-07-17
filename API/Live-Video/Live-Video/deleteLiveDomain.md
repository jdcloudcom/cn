# deleteLiveDomain


## 描述
删除直播域名
- 请慎重操作（建议在进行域名删除前到域名解析服务商处恢复域名A记录），以免导致删除操作后此域名不可访问。
  deleteLiveDomain调用成功后将删除本条直播域名的全部相关记录，对于仅需要暂停使用该直播域名，推荐stopLiveDomain接口


## 请求方式
DELETE

## 请求地址
https://live.jdcloud-api.com/v1/domains/{publishDomain}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**publishDomain**|String|True| |推流域名|


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
https://live.jdcloud-api.com/v1/domains:stop
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
