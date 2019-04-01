# deleteCustomLiveStreamRecordTemplate


## 描述
删除用户自定义录制模板
- 删除用户自定义录制模板之前必须先删除此模板在各域名、应用、流级别的录制设置


## 请求方式
DELETE

## 请求地址
https://live.jdcloud-api.com/v1/recordCustoms/{template}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**template**|String|True| |录制模板|

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
https://live.jdcloud-api.com/v1/transcodeCustoms/yourrecordtemplate

```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41"
}
```
