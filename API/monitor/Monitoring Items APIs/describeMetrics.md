# describeMetrics


## 描述
根据产品线查询可用监控项列表

## 请求方式
GET

## 请求地址
https://monitor.jdcloud-api.com/v1/metrics

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**serviceCode**|String|True||资源的类型 ： <br>vm-->云主机<br>disk-->云硬盘<br>ip-->公网ip<br>balance-->负载均衡<br>database-->云数据库mysql版本<br>cdn-->京东CDN<br>redis-->redis云缓存<br>mongodb-->mongoDB云缓存<br>storage-->云存储<br>sqlserver-->云数据库sqlserver版 <br>nativecontainer-->容器<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求的标识id|
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**metrics**|[MetricDetail[]](##MetricDetail)||
### <a name="MetricDetail">MetricDetail</a>
|名称|类型|描述|
|---|---|---|
|**calculateUnit**|String|指标的计算单位，比如bit/s、%、k等|
|**downSample**|String|取样频次|
|**metric**|String|监控项英文标识|
|**metricName**|String|监控项名称|
|**serviceCode**|String|产品线标识|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|invalid parameter|
|**500**|internal server error|

## 请求示例
GET
```

```

## 返回示例
无
