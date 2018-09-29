# describeCCAttackLogDetails


## 描述
查询 CC 攻击日志详情

## 请求方式
GET

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/attacklog:CCDetail

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**endTime**|String|True| |查询的结束时间, UTC 时间, 格式：yyyy-MM-dd'T'HH:mm:ssZ|
|**instanceId**|String|True| |高防实例 ID|
|**pageNumber**|Integer|False| |页码, 默认为1|
|**pageSize**|Integer|False| |分页大小, 默认为10, 取值范围[10, 100]|
|**startTime**|String|True| |开始时间, 只能查询最近 60 天以内的数据, UTC 时间, 格式：yyyy-MM-dd'T'HH:mm:ssZ|
|**subDomain**|String[]|False| |子域名|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**currentCount**|Integer|当前页数量|
|**dataList**|CCAttackLogDetail[]| |
|**totalCount**|Integer|实例总数|
|**totalPage**|Integer|总页数|
### CCAttackLogDetail
|名称|类型|描述|
|---|---|---|
|**key**|String|特征key|
|**num**|Integer|攻击次数|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
