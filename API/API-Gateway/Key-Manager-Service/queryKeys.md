# queryKeys


## 描述
查询key列表

## 请求方式
GET

## 请求地址
https://apigateway.jdcloud-api.com/v1/regions/{regionId}/kms

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False|1|页码, 默认为1, 取值范围：[1,∞)|
|**pageSize**|Integer|False|20|分页大小，默认为20，取值范围：[10,100]|
|**orderBy**|String|False| |排序类型|
|**userType**|String|False| |用户类型|
|**keyId**|String|False| |密钥Id|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](querykeys#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**total**|Integer|total count|
|**data**|[KeyInfo[]](querykeys#keyinfo)|key详情|
### <div id="keyinfo">KeyInfo</div>
|名称|类型|描述|
|---|---|---|
|**userId**|String|userid|
|**keyId**|String|keyid|
|**keyName**|String|keyname|
|**accessKey**|String|ak|
|**secretKey**|String|sk|
|**keyDesc**|String|key描述信息|
|**createTime**|String|创建时间|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
