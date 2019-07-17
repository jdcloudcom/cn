# updateGroup


## 描述
修改用户组

## 请求方式
PUT

## 请求地址
https://iam.jdcloud-api.com/v1/group/{groupName}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**groupName**|String|True| |用户组名称|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**updateGroupInfo**|UpdateGroupInfo|True| | |

### UpdateGroupInfo
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**description**|String|False| |用户组描述|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
