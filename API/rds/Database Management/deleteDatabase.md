# deleteDatabase


## 描述
删除数据库</br>敏感操作，可开启<a href="https://www.jdcloud.com/help/detail/3786/isCatalog/1">MFA操作保护</a>

## 请求方式
DELETE

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/databases/{dbName}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dbName**|String|True||库名称|
|**instanceId**|String|True||实例ID|
|**regionId**|String|True||区域代码|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|



## 返回码
|返回码|描述|
|---|---|
|**200**|OK|

## 请求示例
DELETE
```

```

## 返回示例
无
