# deleteInstance


## 描述
删除数据库集群实例及Mysql只读实例</br>- SQL Server：支持</br>- MySQL：支持</br>敏感操作，可开启<a href="https://www.jdcloud.com/help/detail/3786/isCatalog/1">MFA操作保护</a>

## 请求方式
DELETE

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||Instance ID|
|**regionId**|String|True||Region ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|



## 返回码
|返回码|描述|
|---|---|
|**200**|OK|

## 请求示例
DELETE
```

```

## 返回示例
无
