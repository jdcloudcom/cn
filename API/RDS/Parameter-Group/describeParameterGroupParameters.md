# describeParameterGroupParameters


## 描述
查看参数组的参数<br>- 仅支持MySQL，Percona，MariaDB，PostgreSQL

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/parameterGroups/{parameterGroupId}/parameters

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|
|**parameterGroupId**|String|True| |Parameter Group ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**parameters**|[ParameterGroupParameter[]](#ParameterGroupParameter)| |
### <a name="ParameterGroupParameter">ParameterGroupParameter</a>
|名称|类型|描述|
|---|---|---|
|**name**|String|参数名称|
|**description**|String|参数描述|
|**configureValue**|String|参数修改后的数值，但不一定生效，需要视该参数生效是否需要重启|
|**defaultValue**|String|参数默认值|
|**range**|String|该参数数值的允许修改范围|
|**type**|String|参数数值的类型|
|**needRestart**|String|参数修改是否需要重启生效.- true:参数需要重启才能生效- false:参数生效无需重启|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
