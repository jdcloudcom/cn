# setImportFileShared


## 描述
设置上传文件是否共享给该用户的其他实例</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/importFiles/{fileName}:setShared

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**fileName**|String|True||单库上云文件名|
|**instanceId**|String|True||实例ID|
|**regionId**|String|True||区域编码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**shared**|String|True||文件是否共享，不区分大小写，true:共享;false:不共享|


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
