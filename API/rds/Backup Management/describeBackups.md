# describeBackups


## 描述
获取备份信息</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/backups

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**auto**|Integer|False||查询备份类型，0为手动备份，1为自动备份，不传表示全部. </br><strong>- 测试参数，后续可能被其他参数取代</strong>|
|**backupTimeRangeEndFilter**|String|False||返回备份开始时间小于等于该时间的备份列表，格式为：YYYY-MM-DD HH:mm:ss</br><strong>- 测试参数，后续可能被其他参数取代</strong>|
|**backupTimeRangeStartFilter**|String|False||返回备份开始时间大于该时间的备份列表，格式为：YYYY-MM-DD HH:mm:ss</br><strong>- 测试参数，后续可能被其他参数取代</strong>|
|**backupTypeFilter**|String|False||返回backupType等于指定值的备份列表。full为全量备份，diff为增量备份</br><strong>- 测试参数，后续可能被其他参数取代</strong>|
|**dbNameFilter**|String|False||返回dbName等于指定值的备份列表，不传或为空返回全部</br><strong>- 测试参数，后续可能被其他参数取代</strong>|
|**instanceId**|String|True||实例ID|
|**pageNumber**|Integer|True||显示数据的页码，取值范围：[1,1000)，页码超过总页数时，显示最后一页，用于查询列表的接口|
|**pageSize**|Integer|True||每页显示的数据条数，默认为10，取值范围：[1,100]，只能为10的倍数|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**backup**|[Backup[]](##Backup)|备份集合|
|**totalCount**|Integer|总记录数|
### <a name="Backup">Backup</a>
|名称|类型|描述|
|---|---|---|
|**backupEndTime**|String|备份结束时间，格式为：YYYY-MM-DD HH:mm:ss|
|**backupFiles**|String[]|备份文件列表，仅SQL Server支持该参数，文件名的命名规则为:</br>全备:数据库名+.bak; </br>增量:数据库名+.diff|
|**backupId**|String|备份ID|
|**backupMode**|String|备份模式，系统自动备份或手动备份</br>Automated：自动备份</br>Manual：手工备份|
|**backupName**|String|备份名称|
|**backupSizeByte**|Integer|整个备份集大小，单位：Byte|
|**backupStartTime**|String|备份开始时间，格式为：YYYY-MM-DD HH:mm:ss|
|**backupStatus**|String|备份状态 </br> COMPLETED：备份完成</br>FAILED：备份失败</br>BUILDING：备份中</br>DELETING：删除中|
|**backupType**|String|备份类型，全量备份或增量备份</br>full：全量</br>diff：增量|
|**backupUnit**|String|备份粒度，实例备份或者多库备份</br>instance：实例备份</br>dbs：数据库备份|
|**instanceId**|String|备份所属实例ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|

## 请求示例
GET
```

```

## 返回示例
无
