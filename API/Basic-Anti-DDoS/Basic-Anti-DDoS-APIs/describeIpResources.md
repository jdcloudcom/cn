# describeIpResources


## 描述
查询区域下的公网Ip资源列表

## 请求方式
GET

## 请求地址
https://baseanti.jdcloud-api.com/v1/regions/{regionId}/ipResources

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ip**|String|True||公网ip|
|**regionId**|String|True||Region ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**dataList**|[IpResource[]](##IpResource)||
|**totalCount**|Integer||
### <a name="IpResource">IpResource</a>
|名称|类型|描述|
|---|---|---|
|**bandwidth**|Integer|带宽上限，单位Mbps|
|**ip**|String|公网IP|
|**safeStatus**|Integer|0->安全 1->清洗 2->黑洞|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
