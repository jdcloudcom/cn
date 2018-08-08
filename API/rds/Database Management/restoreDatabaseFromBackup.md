# restoreDatabaseFromBackup


## 描述
从云数据库SQL Server备份中恢复单个数据库</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/databases/{dbName}:restoreDatabaseFromBackup

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dbName**|String|True||库名称|
|**instanceId**|String|True||实例ID|
|**regionId**|String|True||区域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**backupFileName**|String|True||指定该备份中用于恢复数据库的文件名称|
|**backupId**|String|True||备份ID|


## 返回参数
|名称|类型|描述|
|---|---|---|



## 返回码
|返回码|描述|
|---|---|
|**200**|OK|

## 请求示例
POST
```

```

## 返回示例
无
