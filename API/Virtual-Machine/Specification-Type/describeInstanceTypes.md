# describeInstanceTypes


## 描述
查询规格类型信息列表


## 请求方式
GET

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/instanceTypes

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**filters**|[Filter[]](##Filter)|False||instanceTypes - 规格类型，精确匹配，支持多个<br>az - 可用区，精确匹配，支持多个<br>|

### <a name="Filter">Filter</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True||过滤条件的名称|
|**operator**|String|False||过滤条件的操作符，默认eq|
|**values**|String[]|True||过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**instanceTypes**|[InstanceType[]](##InstanceType)|通用的规格类型|
|**specificInstanceTypes**|[InstanceType[]](##InstanceType)|用户特有的规格类型；需要工单申请|
|**totalCount**|Integer|总数量|
### <a name="InstanceType">InstanceType</a>
|名称|类型|描述|
|---|---|---|
|**cpu**|Integer|cpu个数|
|**desc**|String|描述|
|**family**|String|实例族|
|**instanceType**|String|规格类型，比如g.b1.2xlarge|
|**memoryMB**|Integer|内存大小|
|**nicLimit**|Integer|支持弹性网卡的数量|
|**state**|[InstanceTypeState[]](##InstanceTypeState)|规格状态|
### <a name="InstanceTypeState">InstanceTypeState</a>
|名称|类型|描述|
|---|---|---|
|**az**|String|可用区|
|**inStock**|Boolean|可售卖情况，true:可售卖、false:已售罄不可用|

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
