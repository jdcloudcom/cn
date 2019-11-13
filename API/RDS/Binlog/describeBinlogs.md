# describeBinlogs


## 描述
获取MySQL实例中binlog的详细信息<br>- 仅支持 MySQL, Percona, MariaDB

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/binlogs

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageNumber为-1时，返回所有数据页码；超过总页数时，显示最后一页。|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：10、20、30、50、100|
|**startTime**|String|False| |查询开始时间，格式为：YYYY-MM-DD HH:mm:ss，开始时间到结束时间不超过三天|
|**endTime**|String|False| |查询结束时间，格式为：YYYY-MM-DD HH:mm:ss，开始时间到结束时间不超过三天|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**totalCount**|Integer|总记录数|
|**binlogs**|[Binlog[]](#Binlog)|备份集合|
### <a name="Binlog">Binlog</a>
|名称|类型|描述|
|---|---|---|
|**binlogBackupId**|String|binlog日志备份ID|
|**binlogName**|String|binlog日志名称|
|**binlogSizeKB**|Long|binlog日志大小，单位KB|
|**binlogStartTime**|String|binlog开始时间,格式为：YYYY-MM-DD HH:mm:ss|
|**binlogEndTime**|String|binlog结束时间,格式为：YYYY-MM-DD HH:mm:ss|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
