# grantPrivilege


## 描述
数据库账号授权</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/accounts/{accountName}:grantPrivilege

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**accountName**|String|True||账户名|
|**instanceId**|String|True||实例ID|
|**regionId**|String|True||地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**accountPrivileges**|[AccountPrivilege[]](##AccountPrivilege)|True||账号的访问权限|

### <a name="AccountPrivilege">AccountPrivilege</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dbName**|String|False||数据库名称|
|**privilege**|String|False||对数据库具有的权限</br>ro:只读</br>rw:读写|

## 返回参数
|名称|类型|描述|
|---|---|---|



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
