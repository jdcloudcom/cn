# describePermissionDetail


## 描述
查询策略详情

## 请求方式
GET

## 请求地址
https://iam.jdcloud-api.com/v1/regions/{regionId}/permission/{permissionId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**permissionId**|Integer|True| |权限id|
|**regionId**|String|True| |Region ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**permission**|Permission|权限信息|
### Permission
|名称|类型|描述|
|---|---|---|
|**account**|String|主账号pin|
|**content**|String|权限内容|
|**description**|String|描述|
|**id**|Integer|权限id|
|**name**|String|权限名称|
|**permissionDetailList**|PermissionDetail[]|权限详细信息|
|**permissionType**|String|权限类型|
|**version**|String|权限版本号|
### PermissionDetail
|名称|类型|描述|
|---|---|---|
|**permission**|String|权限类型，只读-R、删除-D、修改-M|
|**resource**|Resource[]|资源信息|
### Resource
|名称|类型|描述|
|---|---|---|
|**ids**|String[]|资源id集合，传*表示对所有id生效|
|**type**|String|资源类型，云主机-server、镜像-image、云硬盘-volume、vpc-vpc、公网Ip-floatingIp、负载均衡-loadbalance、云数据库(mysql)-database、云缓存-cache|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
