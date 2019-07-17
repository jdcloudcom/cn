# detachSubUserPolicy


## 描述
为子用户解绑策略

## 请求方式
DELETE

## 请求地址
https://iam.jdcloud-api.com/v1/subUser/{subUser}:detachSubUserPolicy

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**subUser**|String|True| |子用户名|

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
