# alterTableWithOnlineDDL


## 描述
通过 PT-OSC 服务来处理 DDL 命令, 避免锁表。此接口暂是对部分用户开放

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:alterTableWithOnlineDDL

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**database**|String|True| |DDL命令修改的库名|
|**table**|String|True| |DDL命令修改的表名|
|**command**|String|True| |需要执行的的DDL命令|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
