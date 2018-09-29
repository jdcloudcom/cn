# describeInstanceClass


## 描述
查询某区域下的实例规格列表

## 请求方式
GET

## 请求地址
https://redis.jdcloud-api.com/v1/regions/{regionId}/instanceClass

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**instanceClasses**|InstanceClass[]| |
|**totalCount**|Integer| |
### InstanceClass
|名称|类型|描述|
|---|---|---|
|**bandwidthMbps**|Integer|带宽|
|**cpu**|Integer|cpu|
|**diskGB**|Integer|磁盘|
|**instanceClass**|String|实例规格代码,参见实例规格代码表|
|**maxConnetction**|Integer|最大链接数|
|**memoryMB**|Integer|内存|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
