# describeBackupDownloadURL


## 描述
获取备份下载链接</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/backups/{backupId}/downloadURLs

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**backupId**|String|True||备份ID|
|**regionId**|String|True||地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**fileName**|String|False||SQL Server：指定该备份中需要获取下载链接的文件名称，SQL Server必须输入该参数</br>MySQL：无需此参数；|
|**urlExpirationSecond**|String|False||指定下载链接的有效时间，单位秒,缺省为86400秒（即24小时） 取值范围：1-864000|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**internalURL**|String|内网下载链接，若当前不可下载，则为空串|
|**publicURL**|String|公网下载链接，若当前不可下载，则为空串|

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
