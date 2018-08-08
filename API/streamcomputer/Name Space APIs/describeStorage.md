# describeStorage


## 描述
查询指定输入

## 请求方式
GET

## 请求地址
https://streamcomputeapi.jdcloud.com/v1/regions/{regionId}/storage

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**storageId**|Integer|True||storageId|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**data**|[Storage](##Storage)||
### <a name="Storage">Storage</a>
|名称|类型|描述|
|---|---|---|
|**createTime**|String||
|**deleted**|String||
|**id**|Integer||
|**name**|String||
|**namespaceId**|String||
|**storageParameterList**|[StorageParameter[]](##StorageParameter)||
|**storageType**|String||
|**type**|String||
|**uid**|String||
|**updateTime**|String||
|**userName**|String||
### <a name="StorageParameter">StorageParameter</a>
|名称|类型|描述|
|---|---|---|
|**createTime**|String||
|**deleted**|String||
|**id**|Integer||
|**pKey**|String||
|**pValue**|String||
|**storageId**|Integer||
|**uid**|String||
|**updateTime**|String||

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**401**|UNAUTHENTICATED|
|**500**|internal error|

## 请求示例
GET
```

```

## 返回示例
无
