# addPermissionsToSubUser


## 描述
为子用户绑定策略

## 请求方式
POST

## 请求地址
https://iam.jdcloud-api.com/v1/regions/{regionId}/subUser/{subUser}/permisssions

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|
|**subUser**|String|True| |子用户用户名|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**addPermissionsInfo**|AddPermissionsInfo|True| |权限信息|

### AddPermissionsInfo
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**permissionIds**|Integer[]|True| |权限id集合|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
