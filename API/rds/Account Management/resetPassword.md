# resetPassword


## 描述
数据库账号重置密码</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/accounts/{accountName}:resetPassword

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**accountName**|String|True||账户名|
|**instanceId**|String|True||实例ID|
|**regionId**|String|True||地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**accountPassword**|String|True||新密码|


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
