# describeBackups


## 描述
查看备份

## 请求方式
GET

## 请求地址
https://mongodb.jdcloud-api.com/v1/regions/{regionId}/backups

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**filters**|Filter[]|False| |instanceId - 实例ID, 精确匹配<br>backupId - 备份ID, 精确匹配<br>|
|**pageNumber**|Integer|False| |页码；默认为1，取值范围：[1,∞)|
|**pageSize**|Integer|False| |分页大小；默认为10；取值范围[1, 100]|

### Filter
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**backups**|Backup[]| |
|**pageNumber**|Integer| |
|**totalCount**|Integer| |
### Backup
|名称|类型|描述|
|---|---|---|
|**backupEndTime**|String|备份结束时间|
|**backupId**|String|备份ID|
|**backupMode**|String|备份模式，Automated(系统自动备份)、Manual(手动备份)|
|**backupName**|String|备份名称|
|**backupSizeByte**|Integer|整个备份集大小，单位：Byte|
|**backupStartTime**|String|备份开始时间|
|**backupStatus**|String|备份状态，Waiting(等待中)、Running(备份中)、Finished(已完成)、(Failed错误)|
|**instanceId**|String|备份所属实例ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
