# restoreDatabaseFromFile


## 描述
从用户上传的备份文件中恢复SQL Server数据库</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/databases/{dbName}:restoreDatabaseFromFile

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dbName**|String|True||库名称|
|**instanceId**|String|True||实例ID|
|**regionId**|String|True||区域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**fileName**|String|True||用户在单库上云中上传的文件名称|
|**sharedFileGid**|String|False||共享文件的全局ID，可从上传文件查询接口describeImportFiles获取；如果该文件不是共享文件，则全局ID为空|


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
