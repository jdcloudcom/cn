# rebootInstance


## 描述
重启RDS实例，例如修改了一些配置参数后，需要重启实例才能生效。可以结合主备切换的功能，轮流重启备机，降低对业务的影响<br>**注意：如果实例正在进行备份，那么重启主实例将会终止备份操作。** 可以查看备份策略中的备份开始时间确认是否有备份正在运行。如果确实需要在实例备份时重启主实例，建议重启后，手工进行一次实例的全备。

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:rebootInstance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**rebootMaster**|Boolean|False| |是否重启主节点。<br> - 仅SQL Server 支持该参数|
|**rebootSlave**|Boolean|False| |是否重启备节点。<br> - 仅SQL Server 支持该参数|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
