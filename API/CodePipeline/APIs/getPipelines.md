# getPipelines


## 描述
查询获取流水线任务列表，并显示最后一次执行的状态或结果信息


## 请求方式
GET

## 请求地址
https://pipeline.jdcloud-api.com/v1/regions/{regionId}/pipeline

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |页码；默认为1|
|**pageSize**|Integer|False| |分页大小；默认为10；取值范围[10, 100]|
|**sorts**|Sort[]|False| | |
|**filters**|Filter[]|False| |根据流水线名称查询|

### Filter
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|
### Sort
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |排序条件的名称|
|**direction**|String|False| |排序条件的方向|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**totalCount**|Integer| |
|**pipelines**|SimplePipeline[]| |
### SimplePipeline
|名称|类型|描述|
|---|---|---|
|**uuid**|String|流水线的uuid|
|**name**|String|流水线名称|
|**startedAt**|Integer|开始执行流水线的时间|
|**latestStatus**|String|最近一次执行的状态(数据结构待商定)|
|**latestInstanceUuid**|String|最新一次执行的实例ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
