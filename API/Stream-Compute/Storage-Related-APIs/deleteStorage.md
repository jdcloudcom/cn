# deleteStorage


## 描述
删除指定输入

## 请求方式
DELETE

## 请求地址
https://streamcompute.jdcloud-api.com/v1/regions/{regionId}/storage

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**storageId**|Integer|True| |storageId|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**message**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**401**|UNAUTHENTICATED|
|**500**|internal error|
