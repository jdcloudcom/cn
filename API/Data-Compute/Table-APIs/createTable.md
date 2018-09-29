# createTable


## 描述
创建用户实例的数据表

## 请求方式
POST

## 请求地址
https://xdata.jdcloud-api.com/v1/regions/{regionId}/dwTable

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dbModelDBTable**|DwTableDesc|True| |数据表描述信息|
|**instanceName**|String|True| |实例名称|

### DwTableDesc
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**comments**|String|False| |描述信息|
|**createTime**|String|False| |创建时间（自动生成）|
|**dbName**|String|False| |数据库名|
|**externalLocation**|String|False| |外表位置|
|**fieldsDelimit**|String|False| |字段分隔符|
|**hiveFileFormat**|String|False| |存储格式|
|**linesDelimit**|String|False| |行分隔符|
|**otherSerdeProperties**|Object|False| |其他serde属性|
|**owner**|String|False| |所有者（自动生成）|
|**parameters**|Object|False| |参数|
|**rows**|DwTableRow[]|False| |列信息|
|**tableName**|String|False| |表名|
### DwTableRow
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**columnName**|String|False| |字段名称|
|**columnType**|String|False| |字段类型|
|**comments**|String|False| |描述信息|
|**isPartition**|Boolean|False| |是否分区字段|

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
