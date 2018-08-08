# describeErrorLogs


## 描述
获取SQL Server 错误日志及下载信息</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/errorLogs

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
|**errorLogs**|[ErrorLog[]](##ErrorLog)|QL Server 错误日志列表|
### <a name="ErrorLog">ErrorLog</a>
|名称|类型|描述|
|---|---|---|
|**internalURL**|String|内网下载链接|
|**lastUpdateTime**|String|错误日志最后更新时间，格式为：YYYY-MM-DD HH:mm:ss|
|**name**|String|错误日志名称|
|**publicURL**|String|公网下载链接|
|**sizeByte**|Integer|错误日志大小，单位Byte|
|**uploadTime**|String|错误日志上传时间，格式为：YYYY-MM-DD HH:mm:ss|

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
