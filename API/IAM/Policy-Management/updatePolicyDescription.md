# updatePolicyDescription


## 描述
修改策略描述

## 请求方式
PUT

## 请求地址
https://iam.jdcloud-api.com/v1/policy/{policyName}/description

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**policyName**|String|True| |策略名称|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**updatePolicyDescriptionInfo**|UpdatePolicyDescriptionInfo|True| |策略描述信息|

### UpdatePolicyDescriptionInfo
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**description**|String|True| |描述，0~256个字符|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
