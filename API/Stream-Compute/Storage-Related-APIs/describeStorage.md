# describeStorage


## 描述
查询指定输入

## 请求方式
GET

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
|**data**|Storage| |
### Storage
|名称|类型|描述|
|---|---|---|
|**createTime**|String| |
|**deleted**|String| |
|**id**|Integer| |
|**name**|String| |
|**namespaceId**|String| |
|**storageParameterList**|StorageParameter[]|Storage的具体参数。<br>1、创建源类型为流式数据输入时，则需要传输source，topicName，duration，format，delimiter，schema 。<br> 2、创建输出如果输出位置为流数据总线，需要传topicName，format，delimiter，ossFlag，bucketName，directory，objectName。<br>3、创建输出如果输出位置为数据计算服务，则需要传输database，table，ossFlag，bucketName，directory，objectName。|
|**storageType**|String|这个参数有input和ouput两个可选值，取决于创建输入还是输出|
|**type**|String| |
|**uid**|String| |
|**updateTime**|String| |
|**userName**|String| |
### StorageParameter
|名称|类型|描述|
|---|---|---|
|**createTime**|String| |
|**deleted**|String| |
|**id**|Integer| |
|**pKey**|String| |
|**pValue**|String| |
|**storageId**|Integer| |
|**uid**|String| |
|**updateTime**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**401**|UNAUTHENTICATED|
|**500**|internal error|
