# describeAuditDownloadURL


## 描述
获取某个审计文件的下载链接，同时支持内链和外链，链接的有效时间为24小时<br>- 仅支持SQL Server

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/audit:describeAuditDownloadURL

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**fileName**|String|True| |审计文件名|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**publicURL**|String|公网下载链接，若当前不可下载，则为空串|
|**internalURL**|String|内网下载链接，若当前不可下载，则为空串|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
