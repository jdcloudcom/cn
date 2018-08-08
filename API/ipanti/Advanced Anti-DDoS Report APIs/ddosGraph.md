# ddosGraph


## 描述
ddos防护报表

## 请求方式
GET

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/charts:ddosGraph

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**endTime**|String|True||查询的结束时间，UTC时间，格式：yyyy-MM-dd'T'HH:mm:ssZ|
|**instanceId**|String[]|False||高防实例id，可以传0个或多个|
|**startTime**|String|True||开始时间，最多查最近30天，UTC时间，格式：yyyy-MM-dd'T'HH:mm:ssZ|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**postProtect**|Number[]||
|**preProtect**|Number[]||
|**time**|Integer[]||
|**unit**|String|单位|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|

## 请求示例
GET
```

```

## 返回示例
无
