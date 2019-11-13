# describeActiveQueryPerformance


## 描述
根据用户定义的查询条件，获取正在执行中的SQL执行的性能信息。用户可以根据这些信息查找与SQL执行相关的性能瓶颈，并进行优化。<br>- 仅支持SQL Server

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/performance:describeActiveQueryPerformance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**db**|String|False| |需要查询的数据库名，多个数据库名之间用英文逗号分隔，默认所有数据库|
|**threshold**|Integer|False| |返回执行时间大于等于threshold的记录，默认10，单位秒|
|**pageNumber**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,1000)。pageNumber为-1时，返回所有数据页码；超过总页数时，显示最后一页。|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为50，取值范围：[1,100]，只能为10的倍数|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**activeQueryPerformanceResult**|[ActiveQueryPerformanceResult[]](#ActiveQueryPerformanceResult)|查询性能统计结果集|
|**totalCount**|Integer|总记录条数|
|**pageNumber**|Integer|当前数据的页码|
|**pageSize**|Integer|每页显示的数据条数|
### <a name="ActiveQueryPerformanceResult">ActiveQueryPerformanceResult</a>
|名称|类型|描述|
|---|---|---|
|**sql**|String|sql语句|
|**startTime**|String|开始执行时间，格式为YYYY-MM-DD hh:mm:ss|
|**elapsedTime**|Integer|执行时长，单位秒|
|**db**|String|数据库名|
|**sessionId**|String|该SQL执行时的Session ID|
|**user**|String|执行该SQL的用户名|
|**status**|String|SQL 的执行状态|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
