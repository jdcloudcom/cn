# modifyInstanceSpec


## 描述
变更实例规格

## 请求方式
POST

## 请求地址
https://mongodb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:modifyInstanceSpec

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |Instance ID|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceClass**|String|True| |实例规格，包年包月不允许小于当前规格。|
|**instanceStorageGB**|Integer|True| |存储空间，包年包月不允许小于当前规格。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**instanceId**|String| |
|**orderId**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
