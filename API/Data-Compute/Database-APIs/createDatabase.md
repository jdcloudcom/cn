# createDatabase


## 描述
创建属于用户实例的数据库

## 请求方式
POST

## 请求地址
https://xdata.jdcloud-api.com/v1/regions/{regionId}/dwDatabase/{databaseName}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**databaseName**|String|True| |数据库名|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**description**|String|False| |数据库描述信息|
|**instanceName**|String|True| |实例名称|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**message**|String| |
|**status**|Boolean| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
