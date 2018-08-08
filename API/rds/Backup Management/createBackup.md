# createBackup


## 描述
创建备份</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/backups

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**backupSpec**|[BackupSpec](##BackupSpec)|False||备份规格|
|**instanceId**|String|False||集群ID|

### <a name="BackupSpec">BackupSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**backupName**|String|False||备份名称，缺省系统将分配一个随机名称|
|**dbNames**|String[]|False||需要备份的数据库名称列表。如不填，则备份整个实例。</br>SQL Server支持该参数</br><strong>MySQL不支持该参数</strong>|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**backupId**|String|备份Id|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|

## 请求示例
POST
```

```

## 返回示例
无
