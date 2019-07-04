# queryDomainLog


## 描述
查询日志

## 请求方式
GET

## 请求地址
https://cdn.jdcloud-api.com/v1/domain/{domain}/log

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domain**|String|True| |用户域名|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**startTime**|String|False| |查询起始时间,UTC时间，格式为:yyyy-MM-dd'T'HH:mm:ss'Z'，示例:2018-10-21T10:00:00Z|
|**endTime**|String|False| |查询截止时间,UTC时间，格式为:yyyy-MM-dd'T'HH:mm:ss'Z'，示例:2018-10-21T10:00:00Z|
|**interval**|String|False| |时间间隔，取值(hour，day，fiveMin)，不传默认小时。|
|**logType**|String|False| |日志类型，取值(log，zip,gz)，不传默认gz。|
|**pageSize**|Integer|False| |页面大小，默认值10|
|**pageNumber**|Integer|False| |分页页数，默认值1|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**total**|Integer|总的数量|
|**pageSize**|Integer|页面大小|
|**pageNumber**|Integer|页面页数|
|**urls**|DomainLog[]| |
### DomainLog
|名称|类型|描述|
|---|---|---|
|**url**|String|下载链接|
|**md5**|String|md5值|
|**fileName**|String|文件名|
|**size**|Long|文件大小|
|**startTime**|String|日志开始时间，UTC时间|
|**endTime**|String|日志结束时间，UTC时间|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
