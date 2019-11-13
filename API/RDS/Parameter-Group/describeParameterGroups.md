# describeParameterGroups


## 描述
获取当前账号下所有的参数组列表<br>- 仅支持MySQL，Percona，MariaDB，PostgreSQL

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/parameterGroups

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageNumber为-1时，返回所有数据页码；超过总页数时，显示最后一页;|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[10,100]，且为10的整数倍|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**parameterGroups**|[ParameterGroup[]](#ParameterGroup)| |
|**totalCount**|Integer| |
### <a name="ParameterGroup">ParameterGroup</a>
|名称|类型|描述|
|---|---|---|
|**parameterGroupId**|String|参数组ID|
|**parameterGroupName**|String|参数组名称|
|**parameterGroupStatus**|String|参数组状态|
|**description**|String|参数组描述|
|**engine**|String|实例引擎类型|
|**engineVersion**|String|数据库版本|
|**regionId**|String|地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**createTime**|String|参数组创建时间|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
