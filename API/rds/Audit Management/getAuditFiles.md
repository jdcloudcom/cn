# getAuditFiles


## 描述
查看审计文件列表</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/audit:getAuditFiles

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||Instance ID|
|**regionId**|String|True||Region ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**auditFiles**|[AuditFile[]](##AuditFile)||
### <a name="AuditFile">AuditFile</a>
|名称|类型|描述|
|---|---|---|
|**lastUpdateTime**|String|审计日志最后更新时间|
|**name**|String|审计日志名称|
|**sizeByte**|Integer|审计日志大小，单位Byte|
|**uploadTime**|String|审计日志上传时间|

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
