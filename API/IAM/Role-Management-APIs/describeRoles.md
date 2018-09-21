# describeRoles


## 描述
查询角色列表

## 请求方式
GET

## 请求地址
https://iam.jdcloud-api.com/v1/roles

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False|1|页码|
|**pageSize**|Integer|False|50|每页显示数目[10~100] 默认50条|
|**pathPrefix**|String|False||path前缀|
|**roleName**|String|False||角色名称关键词|
|**sort**|Integer|True||排序策略,0-按创建时间顺序排序  1-按创建时间倒序|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|Result||


### Result
|名称|类型|描述|
|---|---|---|
|**roles**|ListRoleInfo[]|角色列表|
|**total**|Integer|总数|
### ListRoleInfo
|名称|类型|描述|
|---|---|---|
|**createTime**|String|创建角色的时间|
|**description**|String|描述，0~1000个字符|
|**roleName**|String|角色名称|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
