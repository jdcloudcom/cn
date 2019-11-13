# describeBinlogDownloadURL


## 描述
获取MySQL实例的binlog的下载链接<br>- 仅支持 MySQL, Percona, MariaDB

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/binlogs/{binlogBackupId}:describeBinlogDownloadURL

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**binlogBackupId**|String|True| |binlog的备份ID，可以通过describeBinlogs获得|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**seconds**|Integer|False| |设置链接地址的过期时间，单位是秒，默认值是 300 秒，最长不能超过取值范围为 1 ~ 86400 秒|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**publicURL**|String|公网下载链接|
|**internalURL**|String|内网下载链接|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
