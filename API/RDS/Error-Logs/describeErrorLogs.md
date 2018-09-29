# describeErrorLogs


## 描述
获取SQL Server 错误日志及下载信息<br>- 仅支持SQL Server

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/errorLogs

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**errorLogs**|ErrorLog[]|错误日志文件的集合|
### ErrorLog
|名称|类型|描述|
|---|---|---|
|**internalURL**|String|内网下载链接|
|**lastUpdateTime**|String|错误日志最后更新时间，格式为：YYYY-MM-DD HH:mm:ss|
|**name**|String|错误日志文件名称|
|**publicURL**|String|公网下载链接|
|**sizeByte**|Integer|错误日志文件大小，单位Byte|
|**uploadTime**|String|错误日志上传时间，格式为：YYYY-MM-DD HH:mm:ss|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
