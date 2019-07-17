# createGroup


## 描述
创建用户组

## 请求方式
POST

## 请求地址
https://iam.jdcloud-api.com/v1/group


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**createGroupInfo**|CreateGroupInfo|True| | |

### CreateGroupInfo
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |群组名：支持4-32位的字母，数字以及-和_, 以字母开头|
|**description**|String|False| |描述，0~256个字符|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**group**|CreateGroupRes|用户组信息|
### CreateGroupRes
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
