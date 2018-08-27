# describeDatabases


## 描述
查看数据库列表</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/databases

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||实例ID|
|**regionId**|String|True||区域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dbName**|String|False||数据库名称|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**databases**|[Database[]](##Database)||
### <a name="Database">Database</a>
|名称|类型|描述|
|---|---|---|
|**accessPrivilege**|[DBAccessPrivilege[]](##DBAccessPrivilege)|该数据库相关账户权限列表|
|**characterSetName**|String|字符集名称,mysql字符集包括：utf8；SQL Server字符集包括：Chinese_PRC_CI_AS、Chinese_PRC_CS_AS、SQL_Latin1_General_CP1_CI_AS、SQL_Latin1_General_CP1_CS_AS、Chinese_PRC_BIN|
|**dbName**|String|数据库名称|
|**dbStatus**|String|数据库状态,具体可参考文档 [枚举类型定义](../Enum-Definitions/Enum-Definitions.md)|
### <a name="DBAccessPrivilege">DBAccessPrivilege</a>
|名称|类型|描述|
|---|---|---|
|**accountName**|String|账号名称|
|**privilege**|String|对数据库具有的权限,ro:只读  rw:读写|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
