# describeCcAttackLogDetails


## 描述
查询cc攻击日志详情

## 请求方式
GET

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/attacklog:ccDetail

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**endTime**|String|True||查询的结束时间，UTC时间，格式：yyyy-MM-dd'T'HH:mm:ssZ|
|**instanceId**|String|True||高防实例id|
|**pageNumber**|Integer|False||页码；默认为1|
|**pageSize**|Integer|False||分页大小；默认为10；取值范围[10, 100]|
|**startTime**|String|True||开始时间，最多查最近30天，UTC时间，格式：yyyy-MM-dd'T'HH:mm:ssZ|
|**subDomain**|String[]|False||子域名|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**dataList**|[CCAttackLogDetail[]](##CCAttackLogDetail)||
|**totalCount**|Integer||
### <a name="CCAttackLogDetail">CCAttackLogDetail</a>
|名称|类型|描述|
|---|---|---|
|**key**|String|特征key|
|**num**|Integer|攻击次数|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
