# describeBackupSynchronicities


## 描述
查询跨地域备份同步服务列表。

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/backupSynchronicities

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |显示数据的页码，默认为1，取值范围：[1,∞)，页码超过总页数时，显示最后一页，用于查询列表的接口|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：10、20、30、50、100|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**backupSynchronicities**|[BackupSynchronicity[]](#BackupSynchronicity)| |
|**totalCount**|Integer| |
### <a name="BackupSynchronicity">BackupSynchronicity</a>
|名称|类型|描述|
|---|---|---|
|**serviceId**|String|跨地域备份同步服务ID|
|**instanceId**|String|RDS 实例ID|
|**serviceStatus**|String|跨地域备份同步服务状态，正常，running；错误，error|
|**srcRegion**|String|源实例所在地域|
|**destRegion**|String|备份同步的目标地域|
|**engine**|String|数据库类型|
|**engineVersion**|String|数据库版本|
|**createTime**|String|创建时间|
|**newestDataTime**|String|跨地域备份的最新数据时间点|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
