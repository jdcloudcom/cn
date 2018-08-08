# createDatabase


## 描述
创建数据库</br>- SQL Server：支持</br>- MySQL：暂不支持

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/databases

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||实例ID|
|**regionId**|String|True||区域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**characterSetName**|String|True||字符集名称</br><strong>mysql字符集支持：</strong></br>- utf8；</br><strong>SQL Server字符集支持：</strong></br>- Chinese_PRC_CI_AS</br>- Chinese_PRC_CS_AS</br>- SQL_Latin1_General_CP1_CI_AS</br>- SQL_Latin1_General_CP1_CS_AS</br>- Chinese_PRC_BIN|
|**dbName**|String|True||数据库名称|


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
