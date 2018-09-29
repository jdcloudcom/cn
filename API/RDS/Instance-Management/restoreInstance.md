# restoreInstance


## 描述
使用实例的全量备份覆盖恢复当前实例<br>- 仅支持MySQL

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:restoreInstance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**backupId**|String|False| |用于恢复的备份Id，仅限于本实例生成的备份|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
