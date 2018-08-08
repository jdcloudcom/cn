# describeQueryPerformance


## 描述
查询性能统计</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/performance:describeQueryPerformance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||Instance ID|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False||显示数据的页码，取值范围：[1,1000)，页码超过总页数时，显示最后一页，用于查询列表的接口|
|**pageSize**|Integer|False||每页显示的数据条数，默认为50，取值范围：[1,100]，只能为10的倍数|
|**queryType**|String|True||查询类型，不同的查询类型按照相应的字段从高到低返回结果。支持如下类型：ExecutionCount：执行次数LastRows：上次返回行数ElapsedTime：平均执行时间CPUTime：平均CPU时间LogicalReads：平均逻辑读LogicalWrites：平均逻辑写PhysicalReads：平均物理读|
|**threshold**|Integer|False||只返回查询条件大于等于threshold的记录，默认为0|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**pageNumber**|Integer|当前页码|
|**pageSize**|Integer|每页显示的数据条数|
|**queryPerformanceResult**|[QueryPerformanceResult[]](##QueryPerformanceResult)|查询性能统计结果集|
|**totalCount**|Integer|总记录数|
### <a name="QueryPerformanceResult">QueryPerformanceResult</a>
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

## 请求示例
POST
```

```

## 返回示例
无
