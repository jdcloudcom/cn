# modifyParameterGroup


## 描述
修改RDS实例的参数组<br>- 仅支持MySQL

## 请求方式
PUT

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:modifyParameterGroup

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**parameterGroupId**|String|True| |参数组ID|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
