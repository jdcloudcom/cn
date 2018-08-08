# deleteSnapshot


## 描述
删除单个云硬盘快照:快照状态必须为 available 或 error 状态

## 请求方式
DELETE

## 请求地址
https://disk.jdcloud-api.com/v1/regions/{regionId}/snapshots/{snapshotId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||地域ID|
|**snapshotId**|String|True||快照ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|



## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|

## 请求示例
DELETE
```

```

## 返回示例
无
