# describeMetricData


## 描述
查看某资源监控数据，需指定监控指标和时间范围。

## 请求方式
GET

## 请求地址
https://monitor.jdcloud-api.com/v1/regions/{regionId}/metrics/{metric}/metricData

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**metric**|String|True| |监控项英文标识(id)|
|**regionId**|String|True| |地域 Id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**endTime**|String|False| |查询时间范围的结束时间， UTC时间，格式：2016-12- yyyy-MM-dd'T'HH:mm:ssZ（为空时，将由startTime与timeInterval计算得出）|
|**resourceId**|String|True| |资源的uuid|
|**serviceCode**|String|True| |资源的类型，取值vm, lb, ip, database 等|
|**startTime**|String|False| |查询时间范围的开始时间， UTC时间，格式：yyyy-MM-dd'T'HH:mm:ssZ（默认为当前时间，早于30d时，将被重置为30d）|
|**tags**|TagFilter[]|False| |自定义标签|
|**timeInterval**|String|False| |时间间隔：1h，6h，12h，1d，3d，7d，14d，固定时间间隔，timeInterval 与 endTime 至少填一项|

### TagFilter
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**key**|String|True| |Tag键|
|**values**|String[]|True| |Tag值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求的标识id|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**metricDatas**|MetricData[]| |
### MetricData
|名称|类型|描述|
|---|---|---|
|**data**|DataPoint[]| |
|**metric**|Metric| |
### DataPoint
|名称|类型|描述|
|---|---|---|
|**timestamp**|Integer|时间戳|
|**value**|String|值|
### Metric
|名称|类型|描述|
|---|---|---|
|**calculateUnit**|String|指标的计算单位，比如bit/s、%、k等|
|**metric**|String|监控项英文标识|
|**metricName**|String|监控项名称|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|invalid parameter|
|**500**|internal server error|
