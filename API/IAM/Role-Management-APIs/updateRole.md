# updateRole


## 描述
修改角色基本信息

## 请求方式
PUT

## 请求地址
https://iam.jdcloud-api.com/v1/role/{roleName}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**roleName**|String|True| |角色名称|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**updateRoleInfo**|UpdateRoleInfo|True| |角色信息|

### UpdateRoleInfo
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**description**|String|False| |描述，0~256个字符|
|**maxSessionDuration**|Integer|False| |最大会话时长3600~43200秒，默认3600秒|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |



## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
