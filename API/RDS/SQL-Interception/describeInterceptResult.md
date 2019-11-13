# describeInterceptResult


## 描述
查看开启高安全模式后，当前实例的 SQL 拦截记录<br>- 仅支持MySQL

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/intercept:describeInterceptResult

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|
|**instanceId**|String|True| |Instance ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageNumber为-1时，返回所有数据页码；超过总页数时，显示最后一页;|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[10,100]，且为10的整数倍|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**interceptResult**|[InterceptResult[]](#InterceptResult)| |
|**totalCount**|Integer| |
### <a name="InterceptResult">InterceptResult</a>
|名称|类型|描述|
|---|---|---|
|**startTime**|String|SQL开始执行时间|
|**ip**|String|源IP|
|**accountName**|String|账号名|
|**threadId**|String|线程ID|
|**dbName**|String|数据库名|
|**sql**|String|sql语句|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
