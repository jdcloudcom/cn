# getLogs


## 描述
查询容器日志

## 请求方式
GET

## 请求地址
https://nc.jdcloud-api.com/v1/regions/{regionId}/containers/{containerId}:getLogs

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**containerId**|String|True||Container ID|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**limitBytes**|Integer|False|||
|**sinceSeconds**|Integer|False|||
|**tailLines**|Integer|False|||


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**logs**|Object||

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|

## 请求示例
GET
```

```

## 返回示例
无
