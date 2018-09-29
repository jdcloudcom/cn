# modifyInstanceName


## 描述
修改实例名称

## 请求方式
POST

## 请求地址
https://mongodb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:modifyInstanceName

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |Instance ID|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceName**|String|True| |新的实例名称，只支持数字、字母、英文下划线、中文，且不少于2字符不超过32字符。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
