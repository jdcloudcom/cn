# describeRolePolicies


## 描述
查询角色授权策略列表

## 请求方式
GET

## 请求地址
https://iam.jdcloud-api.com/v1/role/{roleName}/policies

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**roleName**|String|True||角色名称|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**keyword**|String|False||关键字|
|**pageNumber**|Integer|False|1|页码|
|**pageSize**|Integer|False|50|每页显示数目[10~100] 默认50条|
|**sort**|Integer|True||排序策略,0-按创建时间顺序排序  1-按创建时间倒序|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|Result||


### Result
|名称|类型|描述|
|---|---|---|
|**policies**|RolePolicy[]|角色授权列表|
|**total**|Integer|总数|
### RolePolicy
|名称|类型|描述|
|---|---|---|
|**description**|String|描述|
|**policyJrn**|String|权限资源描|
|**policyName**|String|权限名称|
|**type**|String|权限类型|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
