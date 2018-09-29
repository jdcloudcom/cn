# createRole


## 描述
创建角色

## 请求方式
POST

## 请求地址
https://iam.jdcloud-api.com/v1/role

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**createRoleInfo**|CreateRoleInfo|True| |角色信息|

### CreateRoleInfo
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**assumeRolePolicyDocument**|String|True| |角色代入policy|
|**description**|String|False| |描述，0~256个字符|
|**maxSessionDuration**|Integer|False| |最大会话时长3600~43200秒，默认3600秒|
|**path**|String|False| |角色路径|
|**roleName**|String|True| |角色名称|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**roleInfo**|RoleInfo|角色信息|


### RoleInfo
|名称|类型|描述|
|---|---|---|
|**roleInfo**|RoleInfo| |
### RoleInfo
|名称|类型|描述|
|---|---|---|
|**account**|String|角色所属主账号|
|**assumeRolePolicyDocument**|String|角色代入policy|
|**createTime**|String|创建角色的时间|
|**description**|String|描述，0~256个字符|
|**jrn**|String|资源描述|
|**maxSessionDuration**|Integer|最大会话时长3600~43200秒，默认3600秒|
|**path**|String|角色路径|
|**roleId**|String|角色ID|
|**roleName**|String|角色名称|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
