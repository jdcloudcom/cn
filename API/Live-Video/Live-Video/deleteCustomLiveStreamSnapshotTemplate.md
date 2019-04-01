# deleteCustomLiveStreamSnapshotTemplate


## 描述
删除用户自定义直播截图模板
- 删除截图模板前,请先删除此模板相关的截图配置,否则将会影响线上业务


## 请求方式
DELETE

## 请求地址
https://live.jdcloud-api.com/v1/snapshotCustoms/{template}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**template**|String|True| |截图模板|

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
https://live.jdcloud-api.com/v1/snapshotCustoms/yoursnapshottemplate

```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41"
}
```
