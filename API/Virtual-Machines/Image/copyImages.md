# copyImages


## 描述
镜像跨区复制，将私有镜像复制到其它地域下，只允许操作您的个人私有镜像。<br>
只支持rootDeviceType为cloudDisk的云硬盘系统盘镜像操作。


## 请求方式
POST

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/images:copyImages

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**destinationRegion**|String|True| |目标区域|
|**sourceImageIds**|String[]|True| |源镜像ID|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**copyImages**|CopyImage[]|源镜像与目标镜像映射关系|
### CopyImage
|名称|类型|描述|
|---|---|---|
|**destinationImageId**|String|复制后的目标镜像ID|
|**sourceImageId**|String|源镜像ID|

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
