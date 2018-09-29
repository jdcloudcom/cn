# modifyInstanceNetworkAttribute


## 描述
修改虚机弹性网卡属性，包括是否随云主机一起删除。<br>
不能修改主网卡。


## 请求方式
POST

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:modifyInstanceNetworkAttribute

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |云主机ID|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**networks**|InstanceNetworkAttribute[]|False| |弹性网卡列表|

### InstanceNetworkAttribute
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**autoDelete**|Boolean|False| |随主机自动删除，默认为False|
|**networkInterfaceId**|String|False| |弹性网卡ID|

## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
