# describeGroup


## 描述
查询用户组详情

## 请求方式
GET

## 请求地址
https://iam.jdcloud-api.com/v1/group/{groupName}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**groupName**|String|True| |用户组名称|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**group**|GroupDetail|用户组信息|
### GroupDetail
|名称|类型|描述|
|---|---|---|
|**groupId**|String|用户组ID|
|**name**|String|用户组名|
|**jrn**|String|京东云资源标识(jrn)|
|**description**|String|用户组描述|
|**createTime**|String|用户组创建时间|
|**updateTime**|String|用户组更新时间|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
