# describeRole


## 描述
查询角色详情

## 请求方式
GET

## 请求地址
https://iam.jdcloud-api.com/v1/role/{roleName}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**roleName**|String|True| |角色名称|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**roleInfo**|RoleInfo|角色信息|
### RoleInfo
|名称|类型|描述|
|---|---|---|
|**path**|String|角色路径|
|**roleId**|String|角色ID|
|**roleName**|String|角色名称|
|**type**|Integer|角色类型，2-服务相关角色，3-服务角色，4-用户角色|
|**assumeRolePolicyDocument**|String|信任实体信息|
|**description**|String|描述，0~256个字符|
|**maxSessionDuration**|Integer|最大会话时长3600~43200秒，默认3600秒|
|**jrn**|String|京东云资源标识(jrn)|
|**createTime**|String|创建角色的时间|
|**account**|String|角色所属主账号|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
