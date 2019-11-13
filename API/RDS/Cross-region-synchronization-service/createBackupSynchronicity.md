# createBackupSynchronicity


## 描述
创建一个跨地域备份同步服务。

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/backupSynchronicities

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |源实例ID|
|**destRegion**|String|True| |备份同步的目标地域|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**serviceId**|String|跨地域备份同步服务ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
