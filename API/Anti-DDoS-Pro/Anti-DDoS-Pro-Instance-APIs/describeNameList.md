# describeNameList


## 描述
查询高防实例名称列表

## 请求方式
GET

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instance/describeNameList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**id**|String|False| |高防实例 ID, 为空则查询所有实例名称|
|**name**|String|False| |实例名称, 可模糊匹配|
|**pageNumber**|Integer|False| |页码, 默认为 1|
|**pageSize**|Integer|False| |分页大小, 默认为 10, 取值范围 [0, 100]|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**currentCount**|Integer|当前页数量|
|**dataList**|InstanceIdName[]| |
|**totalCount**|Integer|实例总数|
|**totalPage**|Integer|总页数|
### InstanceIdName
|名称|类型|描述|
|---|---|---|
|**id**|String|实例id|
|**name**|String|实例名称|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
