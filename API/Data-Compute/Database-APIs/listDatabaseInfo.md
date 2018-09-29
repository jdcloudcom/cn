# listDatabaseInfo


## 描述
查询用户实例的所有数据库信息

## 请求方式
GET

## 请求地址
https://xdata.jdcloud-api.com/v1/regions/{regionId}/dwDatabase

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
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
|**data**|DwDatabaseInfo[]| |
|**message**|String| |
|**status**|Boolean| |
### DwDatabaseInfo
|名称|类型|描述|
|---|---|---|
|**comments**|String|描述信息|
|**databaseName**|String|数据库名称|
|**owner**|String|所有者|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
