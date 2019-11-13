# modifyParameterGroupAttribute


## 描述
修改参数组名称，描述<br>- 仅支持MySQL，Percona，MariaDB，PostgreSQL

## 请求方式
PUT

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/parameterGroups/{parameterGroupId}:modifyParameterGroupAttribute

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|
|**parameterGroupId**|String|True| |Parameter Group ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**parameterGroupName**|String|True| |参数组名称|
|**description**|String|False| |参数组描述|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
