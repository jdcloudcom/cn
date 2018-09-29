# describeKeypairs


## 描述
批量查询密钥对。<br>
此接口支持分页查询，默认每页20条。


## 请求方式
GET

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/keypairs

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**filters**|Filter[]|False| |keyNames - 密钥对名称，精确匹配，支持多个<br>|
|**pageNumber**|Integer|False|1|页码；默认为1|
|**pageSize**|Integer|False|20|分页大小；默认为20；取值范围[10, 100]|

### Filter
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**keypairs**|Keypair[]| |
|**totalCount**|Number|总的数据条数|
### Keypair
|名称|类型|描述|
|---|---|---|
|**createTime**|String|创建时间|
|**keyFingerprint**|String|密钥对的指纹，根据 RFC4716 定义的公钥指纹格式，采用 MD5 信息摘要算法。|
|**keyName**|String|密钥对名称|

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
