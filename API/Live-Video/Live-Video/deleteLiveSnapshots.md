# deleteLiveSnapshots


## 描述
删除截图


## 请求方式
DELETE

## 请求地址
https://live.jdcloud-api.com/v1/snapshots


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**imgIds**|String|True| |需要删除的截图ID，多个时以逗号（,）分隔<br>|


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
https://live.jdcloud-api.com/v1/snapshots?imgIds=aaa,bbb,ccc

```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41"
}
```
