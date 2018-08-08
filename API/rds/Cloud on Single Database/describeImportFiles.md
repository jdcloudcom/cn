# describeImportFiles


## 描述
获取单库上云文件列表</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/importFiles

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||实例ID|
|**regionId**|String|True||区域编码|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**importFiles**|[ImportFile[]](##ImportFile)|导入文件的集合|
### <a name="ImportFile">ImportFile</a>
|名称|类型|描述|
|---|---|---|
|**isLocal**|String|是否所属当前实例. “true”或者“false”|
|**name**|String|上传的备份文件名称|
|**sharedFileGid**|String|如果该文件是共享文件，则有全局ID，如不是共享文件，则为空|
|**sizeByte**|Integer|文件大小，单位Byte|
|**uploadTime**|String|文件上传完成时间，格式为：YYYY-MM-DD HH:mm:ss|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|

## 请求示例
GET
```

```

## 返回示例
无
