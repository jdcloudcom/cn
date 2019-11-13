# describeSlowLogAttributes


## 描述
查询MySQL实例的慢日志的详细信息。<br>- 仅支持MySQL

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/performance:describeSlowLogAttributes

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**startTime**|String|True| |慢日志开始时间，格式为：YYYY-MM-DD HH:mm:ss，开始时间到当前时间不能大于 7 天, 开始时间不能大于结束时间，结束时间不能大于当前时间|
|**endTime**|String|True| |慢日志结束时间，格式为：YYYY-MM-DD HH:mm:ss，开始时间到当前时间不能大于 7 天, 开始时间不能大于结束时间，结束时间不能大于当前时间|
|**dbName**|String|False| |查询哪个数据库的慢日志，不填表示返回所有数据库的慢日志|
|**pageNumber**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,1000)。pageNumber为-1时，返回所有数据页码；超过总页数时，显示最后一页。|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：10、20、30、50、100|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**slowLogsAttributes**|[SlowLogAttributes[]](#SlowLogAttributes)|慢日志信息|
|**totalCount**|Integer|总记录条数|
### <a name="SlowLogAttributes">SlowLogAttributes</a>
|名称|类型|描述|
|---|---|---|
|**dbName**|String|数据库名，表示该SQL是在哪个数据库中执行的|
|**sql**|String|SQL语句|
|**executionTime**|String|SQL语句执行的开始时间，格式为YYYY-MM-DD hh:mm:ss|
|**elapsedTime**|Float|SQL语句执行的时长，单位秒|
|**lockTime**|Float|SQL语句等待锁的时间，单位秒|
|**rowsExamined**|Integer|SQL语句扫描的行数|
|**rowsReturned**|Integer|SQL语句返回的行数|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
