# addOrUpdateStorage


## 描述
创建或者更新storage

## 请求方式
POST

## 请求地址
https://streamcompute.jdcloud-api.com/v1/regions/{regionId}/storage

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**storageStr**|Storage|True| |创建或者更新storage的详情|

### Storage
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**createTime**|String|False| | |
|**deleted**|String|False| | |
|**id**|Integer|False| | |
|**name**|String|False| | |
|**namespaceId**|String|False| | |
|**storageParameterList**|StorageParameter[]|False| |Storage的具体参数。<br>1、创建源类型为流式数据输入时，则需要传输source，topicName，duration，format，delimiter，schema 。<br> 2、创建输出如果输出位置为流数据总线，需要传topicName，format，delimiter，ossFlag，bucketName，directory，objectName。<br>3、创建输出如果输出位置为数据计算服务，则需要传输database，table，ossFlag，bucketName，directory，objectName。|
|**storageType**|String|False| |这个参数有input和ouput两个可选值，取决于创建输入还是输出|
|**type**|String|False| | |
|**uid**|String|False| | |
|**updateTime**|String|False| | |
|**userName**|String|False| | |
### StorageParameter
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**createTime**|String|False| | |
|**deleted**|String|False| | |
|**id**|Integer|False| | |
|**pKey**|String|False| | |
|**pValue**|String|False| | |
|**storageId**|Integer|False| | |
|**uid**|String|False| | |
|**updateTime**|String|False| | |

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**message**|String| |
|**status**|Boolean| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
|**500**|INTERNAL_ERROR|
|**400**|UNAUTHENTICATED|
