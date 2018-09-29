# describeSecurityIps


## 描述
查询实例访问白名单

## 请求方式
GET

## 请求地址
https://mongodb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/securityIps

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |Instance ID|
|**regionId**|String|True| |Region ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**securityIps**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
