# stopJob


## 描述
停止作业运行job

## 请求方式
GET

## 请求地址
https://streamcomputeapi.jdcloud.com/v1/regions/{regionId}/job:stop

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**jobId**|Integer|True|||
|**namespaceId**|String|True|||


## 返回参数
|名称|类型|描述|
|---|---|---|
|**regionId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**message**|String|成功启动作业返回信息|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|INTERNAL_ERROR|

## 请求示例
GET
```

```

## 返回示例
无
