# describeBackups


## 描述
查看该RDS实例下所有备份的详细信息，返回的备份列表按照备份开始时间（backupStartTime）降序排列。

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/backups

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**auto**|Integer|False| |查询备份类型，0为手动备份，1为自动备份，不传表示全部. <br>**- 测试参数，仅支持SQL Server，后续可能被其他参数取代**|
|**backupTimeRangeEndFilter**|String|False| |返回备份开始时间小于等于该时间的备份列表<br>**- 测试参数，仅支持SQL Server，后续可能被其他参数取代**|
|**backupTimeRangeStartFilter**|String|False| |返回备份开始时间大于该时间的备份列表<br>**- 测试参数，仅支持SQL Server，后续可能被其他参数取代**|
|**backupTypeFilter**|String|False| |返回backupType等于指定值的备份列表。full为全量备份，diff为增量备份<br>**- 测试参数，仅支持SQL Server，后续可能被其他参数取代**|
|**dbNameFilter**|String|False| |返回dbName等于指定值的备份列表，不传或为空返回全部<br>**- 测试参数，仅支持SQL Server，后续可能被其他参数取代**|
|**instanceId**|String|True| |RDS实例ID，唯一标识一个实例|
|**pageNumber**|Integer|True| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageNumber为-1时，返回所有数据页码；超过总页数时，显示最后一页。|
|**pageSize**|Integer|True| |每页显示的数据条数，默认为10，取值范围：10、20、30、50、100|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**backup**|Backup[]|备份集合|
|**totalCount**|Integer|总记录数|
### Backup
|名称|类型|描述|
|---|---|---|
|**backupEndTime**|String|备份结束时间，格式为：YYYY-MM-DD HH:mm:ss<br>- **SQL Server支持**<br>- **MySQL不支持**|
|**backupFiles**|String[]|备份文件列表<br>- **SQL Server支持**,备份可以有多个文件，文件名的命名规则为:<br>（1）全备：数据库名+.bak<br>（2）增量：数据库名+.diff<br>- **MySQL不支持**|
|**backupId**|String|备份ID|
|**backupMode**|String|备份模式，系统自动备份或手动备份，请查看[枚举参数定义](../Enum-Definitions/Enum-Definitions.md)|
|**backupName**|String|备份名称，最长支持64个英文字符或等长的中文字符|
|**backupSizeByte**|Integer|整个备份集大小，单位：Byte|
|**backupStartTime**|String|备份开始时间，格式为：YYYY-MM-DD HH:mm:ss|
|**backupStatus**|String|备份状态，请查看[枚举参数定义](../Enum-Definitions/Enum-Definitions.md)|
|**backupType**|String|备份类型，全量备份或增量备份，请查看[枚举参数定义](../Enum-Definitions/Enum-Definitions.md)<br>- **SQL Server支持**<br>- **MySQL不支持**|
|**backupUnit**|String|备份粒度，实例备份或者多库备份，请查看[枚举参数定义](../Enum-Definitions/Enum-Definitions.md)<br>- **SQL Server支持**<br>- **MySQL不支持**|
|**instanceId**|String|备份所属实例ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
