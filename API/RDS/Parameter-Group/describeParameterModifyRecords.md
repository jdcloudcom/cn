# describeParameterModifyRecords


## 描述
查看参数的修改历史<br>- 仅支持MySQL，Percona，MariaDB，PostgreSQL

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/parameterGroups/{parameterGroupId}/records

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|
|**parameterGroupId**|String|True| |Parameter Group ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageNumber为-1时，返回所有数据页码；超过总页数时，显示最后一页;|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[10,100]，且为10的整数倍|
|**startTime**|String|False| |查询开始时间，格式为：YYYY-MM-DD HH:mm:ss|
|**endTime**|String|False| |查询结束时间，格式为：YYYY-MM-DD HH:mm:ss|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**records**|[ParameterModifyRecords[]](#ParameterModifyRecords)| |
|**totalCount**|Integer| |
### <a name="ParameterModifyRecords">ParameterModifyRecords</a>
|名称|类型|描述|
|---|---|---|
|**name**|String|参数名称|
|**preModify**|String|修改前的参数值|
|**postModify**|String|修改后的参数值|
|**updateTime**|String|修改时间|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
