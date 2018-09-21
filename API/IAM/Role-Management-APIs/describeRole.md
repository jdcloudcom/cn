# describeRole


## 描述
查询角色详情

## 请求方式
GET

## 请求地址
https://iam.jdcloud-api.com/v1/role/{roleName}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**roleName**|String|True||角色名称|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|Result||


### Result
|名称|类型|描述|
|---|---|---|
|**roleInfo**|RoleInfo|角色信息|
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
