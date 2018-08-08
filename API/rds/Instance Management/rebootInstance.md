# rebootInstance


## 描述
重启RDS实例</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:rebootInstance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||Instance ID|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**rebootMaster**|Boolean|False||是否重启主节点。</br>- SQL Server：支持</br>- MySQL：暂不支持|
|**rebootSlave**|Boolean|False||是否重启从节点。</br>- SQL Server：支持</br>- MySQL：暂不支持|


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
