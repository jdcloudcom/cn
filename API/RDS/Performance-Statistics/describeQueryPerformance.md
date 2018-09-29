# describeQueryPerformance


## 描述
根据用户定义的查询条件，获取SQL执行的性能统计信息，例如慢SQL等。用户可以根据这些信息查找与SQL执行相关的性能瓶颈，并进行优化。<br>- 仅支持SQL Server

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/performance:describeQueryPerformance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,1000]。pageNumber为-1时，返回所有数据页码；超过总页数时，显示最后一页。|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为50，取值范围：[1,100]，只能为10的倍数，用于查询列表的接口|
|**queryType**|String|True| |查询类型，不同的查询类型按照相应的字段从高到低返回结果。<br>支持如下类型：<br>ExecutionCount：执行次数<br>LastRows：上次返回行数<br>ElapsedTime：平均执行时间<br>CPUTime：平均CPU时间<br>LogicalReads：平均逻辑读<br>LogicalWrites：平均逻辑写<br>PhysicalReads：平均物理读<br>|
|**threshold**|Integer|False| |只返回查询条件大于等于threshold的记录，默认为0|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**pageNumber**|Integer|当前数据的页码|
|**pageSize**|Integer|每页显示的数据条数|
|**queryPerformanceResult**|QueryPerformanceResult[]|查询性能统计结果集|
|**totalCount**|Integer|总记录条数|
### QueryPerformanceResult
|名称|类型|描述|
|---|---|---|
|**elapsedTime**|Integer|平均执行时长，单位毫秒(ms)|
|**executionCount**|Integer|执行次数|
|**lastExecutionTime**|String|上次执行时间，格式为YYYY-MM-DD hh:mm:ss|
|**lastRows**|Integer|上次返回记录数|
|**logicalReads**|Integer|平均逻辑读次数|
|**logicalWrites**|Integer|平均逻辑写次数|
|**physicalReads**|Integer|平均物理读次数|
|**sql**|String|sql语句|
|**workerTime**|Integer|平均CPU使用时间，单位毫秒(ms)|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
