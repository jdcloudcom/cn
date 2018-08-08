# addOrUpdateStorage


## 描述
创建或者更新storage

## 请求方式
POST

## 请求地址
https://streamcomputeapi.jdcloud.com/v1/regions/{regionId}/storage

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**storageStr**|[Storage](##Storage)|True||创建或者更新storage的详情|

### <a name="Storage">Storage</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**createTime**|String|False|||
|**deleted**|String|False|||
|**id**|Integer|False|||
|**name**|String|False|||
|**namespaceId**|String|False|||
|**storageParameterList**|[StorageParameter[]](##StorageParameter)|False|||
|**storageType**|String|False|||
|**type**|String|False|||
|**uid**|String|False|||
|**updateTime**|String|False|||
|**userName**|String|False|||
### <a name="StorageParameter">StorageParameter</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**createTime**|String|False|||
|**deleted**|String|False|||
|**id**|Integer|False|||
|**pKey**|String|False|||
|**pValue**|String|False|||
|**storageId**|Integer|False|||
|**uid**|String|False|||
|**updateTime**|String|False|||

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**message**|String||
|**status**|Boolean||

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
|**500**|INTERNAL_ERROR|
|**400**|UNAUTHENTICATED|

## 请求示例
POST
```

```

## 返回示例
无
