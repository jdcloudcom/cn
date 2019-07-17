# queryStatisticsDataGroupByArea


## 描述
分地区及运营商查询统计数据

## 请求方式
POST

## 请求地址
https://cdn.jdcloud-api.com/v1/vodStatistics:groupByArea


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**startTime**|String|False| |查询起始时间,UTC时间，格式为:yyyy-MM-dd'T'HH:mm:ss'Z'，示例:2018-10-21T10:00:00Z|
|**endTime**|String|False| |查询截止时间,UTC时间，格式为:yyyy-MM-dd'T'HH:mm:ss'Z'，示例:2018-10-21T10:00:00Z|
|**domain**|String|False| |需要查询的域名, 必须为用户pin下有权限的域名|
|**subDomain**|String|False| |待查询的子域名|
|**fields**|String|False| |需要查询的字段|
|**area**|String|False| | |
|**isp**|String|False| | |
|**origin**|String|False| | |
|**period**|String|False| |时间粒度，可选值:[oneMin,fiveMin,followTime],followTime只会返回一个汇总后的数据|
|**groupBy**|String|False| |分组依据|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**startTime**|String| |
|**endTime**|String| |
|**domain**|String| |
|**statistics**|StatisticsWithAreaGroupDetail[]| |
### StatisticsWithAreaGroupDetail
|名称|类型|描述|
|---|---|---|
|**startTime**|String|UTC时间，格式为:yyyy-MM-dd'T'HH:mm:ss'Z'，示例:2018-10-21T10:00:00Z|
|**endTime**|String|UTC时间，格式为:yyyy-MM-dd'T'HH:mm:ss'Z'，示例:2018-10-21T10:00:00Z|
|**data**|StatisticsWithAreaGroupDetailItem[]| |
### StatisticsWithAreaGroupDetailItem
|名称|类型|描述|
|---|---|---|
|**area**|String| |
|**ispStat**|Object[]| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
