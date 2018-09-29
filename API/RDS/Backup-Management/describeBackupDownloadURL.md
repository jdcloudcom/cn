# describeBackupDownloadURL


## 描述
获取整个备份或备份中单个文件的下载链接。<br>- 当输入参数中有文件名时，获取该文件的下载链接。<br>- 输入参数中无文件名时，获取整个备份的下载链接。<br>由于备份机制的差异，使用该接口下载备份时，SQL Server必须输入文件名，每个文件逐一下载，不支持下载整个备份。SQL Server备份中的文件名（不包括后缀）即为备份的数据库名。例如文件名为my_test_db.bak，表示该文件是my_test_db数据库的备份。<br>MySQL可下载整个备份集，但不支持单个文件的下载。<br>- 仅支持SQL Server

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/backups/{backupId}/downloadURLs

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**backupId**|String|True| |备份ID|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**fileName**|String|False| |文件名称<br>- MySQL：不支持该参数<br>- SQL Server：必须输入该参数，指定该备份中需要获取下载链接的文件名称。备份中的文件名（不包括后缀）即为备份的数据库名。例如文件名为my_test_db.bak，表示该文件是my_test_db数据库的备份|
|**urlExpirationSecond**|String|False| |指定下载链接的过期时间，单位秒,缺省为86400秒，即24小时。<br>- MySQL：不支持该参数，只能是默认值<br>- SQL Server：支持|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**internalURL**|String|内网下载链接，若当前不可下载，则为空串|
|**publicURL**|String|公网下载链接，若当前不可下载，则为空串|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
