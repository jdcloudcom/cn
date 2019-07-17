# updateAssumeRolePolicy


## 描述
修改角色内置policy

## 请求方式
PUT

## 请求地址
https://iam.jdcloud-api.com/v1/role/{roleName}/assumeRolePolicy

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**roleName**|String|True| |角色名称|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**updateAssumeRolePolicyInfo**|UpdateAssumeRolePolicyInfo|True| |角色权限信息|

### UpdateAssumeRolePolicyInfo
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**assumeRolePolicyDocument**|String|False| |信任实体信息|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
