# describeVpcIpList


## 描述
查询用户的京东云 IP 资源

## 请求方式
GET

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instance/describeVpcIpList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |页码, 默认为 1|
|**pageSize**|Integer|False| |分页大小, 默认为 10, 取值范围 [0, 100], 0 表示全量|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**currentCount**|Integer|当前页数量|
|**dataList**|VpcIpResource[]| |
|**totalCount**|Integer|实例总数|
|**totalPage**|Integer|总页数|
### VpcIpResource
|名称|类型|描述|
|---|---|---|
|**binded**|Boolean|是否绑定|
|**ip**|String|云内 IP 地址|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
