# deleteNamespace


## 描述
删除namespace

## 请求方式
DELETE

## 请求地址
https://streamcomputeapi.jdcloud.com/v1/regions/{regionId}/namespace

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**namespaceId**|Integer|True|||


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**status**|Boolean|删除namespace成功标志|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|INTERNAL_ERROR|
|**400**|INTERNAL_ERROR|

## 请求示例
DELETE
```

```

## 返回示例
无
