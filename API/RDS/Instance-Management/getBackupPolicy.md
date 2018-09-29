# getBackupPolicy


## 描述
查看RDS实例备份策略。根据数据库类型的不同，支持的备份策略也略有差异，具体请看返回参数中的详细说明

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:getBackupPolicy

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**backupBinlog**|String|是否备份binlog<br>true:表示备份<br>false:表示不备份<br> - **SQL Server不支持**<br>- **MySQL支持**|
|**cycleMode**|Integer|自动备份循环模式<br>1:表示每天都是全量备份<br>2:表示自动备份按照全量、增量、增量这样的方式进行，例如第1天是全量备份，第2、3天是增量备份；第4天又是全量备份，以此类推.<br>- **SQL Server支持**<br>- **MySQL不支持**|
|**retentionPeriod**|Integer|自动备份保留周期，单位天,缺省为7天，范围7-730|
|**startWindow**|String|自动备份开始时间窗口，范围00:00-23:59，时间范围差不得小于30分钟。<br>例如：00:00-01:00，表示0点到1点开始进行数据库自动备份，备份完成时间则跟实例大小有关，不一定在这个时间范围中|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
