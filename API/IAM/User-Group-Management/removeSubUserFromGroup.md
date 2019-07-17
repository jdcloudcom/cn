# removeSubUserFromGroup


## 描述
将子用户从组中删除

## 请求方式
DELETE

## 请求地址
https://iam.jdcloud-api.com/v1/group/{groupName}:removeSubUserFromGroup

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**groupName**|String|True| |用户组名称|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**subUser**|String|True| |子用户名|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
