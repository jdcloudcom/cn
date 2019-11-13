# describeLatestRestoreTime


## 描述
获取SQL Server实例按时间点恢复/创建时，可恢复到的最后的一个时间点<br>- 仅支持SQL Server

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:describeLatestRestoreTime

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**latestRestoreTime**|String|实例按时间点恢复时,可恢复到的最后的一个时间点|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
