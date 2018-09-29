# describeUserAccessKeys


## 描述
查询AccessKey列表

## 请求方式
GET

## 请求地址
https://iam.jdcloud-api.com/v1/regions/{regionId}/userAccessKeys

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**userAccessKeys**|UserAccessKey[]|userAccessKey列表|
### UserAccessKey
|名称|类型|描述|
|---|---|---|
|**accessKey**|String|accessKey|
|**accessKeySecret**|String|accessKeySecret|
|**createTime**|String|创建时间|
|**state**|Integer|禁用/启用状态[0-禁用,1-启用]|
|**yn**|Integer|删除/有效状态[0-删除,1-有效]|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
