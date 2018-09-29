# getStorageList


## 描述
创建或者更新storage

## 请求方式
GET

## 请求地址
https://streamcompute.jdcloud-api.com/v1/regions/{regionId}/storageList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**namespaceId**|String|True| |namespaceId|
|**storageType**|String|True| |storage类型|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**storageList**|Object[]| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**401**|UNAUTHENTICATED|
