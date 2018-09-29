# getDatabaseInfo


## 描述
查询用户实例的指定数据库信息

## 请求方式
GET

## 请求地址
https://xdata.jdcloud-api.com/v1/regions/{regionId}/dwDatabase/{databaseName}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**databaseName**|String|True| |数据库名|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceName**|String|True| |实例名称|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|DwDatabase| |
|**message**|String| |
|**status**|Boolean| |
### DwDatabase
|名称|类型|描述|
|---|---|---|
|**category**|String|类别|
|**comments**|String|描述信息|
|**createTime**|String|创建时间|
|**databaseName**|String|数据库名称|
|**id**|Integer|数据库id|
|**lastUpdateTime**|String|最新更新时间|
|**location**|String|位置|
|**owner**|String|所有者|
|**physicalStorageCapacity**|String|最新更新时间|
|**source**|String|来源|
|**totalTableQuantity**|Integer|总表数量|
|**userName**|String|用户名|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
