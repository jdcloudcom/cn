# describeAccounts


## 描述
查看实例下所有账号信息</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/accounts

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||实例ID|
|**regionId**|String|True||地域代码|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**accounts**|[Account[]](##Account)||
### <a name="Account">Account</a>
|名称|类型|描述|
|---|---|---|
|**accountName**|String|账号名称|
|**accountPrivileges**|[AccountPrivilege[]](##AccountPrivilege)|账户权限列表|
|**accountStatus**|String|账号状态，building：创建中，running：运行中|
### <a name="AccountPrivilege">AccountPrivilege</a>
|名称|类型|描述|
|---|---|---|
|**dbName**|String|数据库名称|
|**privilege**|String|对数据库具有的权限</br>ro:只读</br>rw:读写|

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
