# attachGroupPolicy


## 描述
为用户组绑定策略

## 请求方式
POST

## 请求地址
https://iam.jdcloud-api.com/v1/group/{groupName}:attachGroupPolicy

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**groupName**|String|True| |用户组名称|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**policyName**|String|True| |策略名称|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
