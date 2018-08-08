# modifyAudit


## 描述
修改当前审计选项</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/audit:modifyAudit

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||Instance ID|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**add**|String|False||增加审计项，多个审计项之间用英文逗号，分号或空格分隔，例如DATABASE_OBJECT_ACCESS_GROUP,ACKUP_RESTORE_GROUP|
|**drop**|String|False||删除审计项，多个审计项之间用英文逗号，分号或空格分隔，例如DATABASE_OBJECT_ACCESS_GROUP,ACKUP_RESTORE_GROUP如删除了所有审计项，则审计自动关闭|


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
