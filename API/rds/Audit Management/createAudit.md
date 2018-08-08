# createAudit


## 描述
开启数据库审计</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/audit

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||Instance ID|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**enabled**|String|True||要开启的审计选项，各个选项之间用英文逗号或空格进行分割，例如：DATABASE_OBJECT_ACCESS_GROUP,ACKUP_RESTORE_GROUP|


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
