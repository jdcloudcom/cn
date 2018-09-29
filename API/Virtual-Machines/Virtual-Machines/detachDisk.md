# detachDisk


## 描述
云主机缷载数据盘，云主机和云硬盘没有正在进行中的任务时才可缷载。<br>


## 请求方式
POST

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:detachDisk

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |云主机ID|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**diskId**|String|True| |云硬盘ID|
|**force**|Boolean|False| |强制缷载，默认False。如果此参数传值为True，代表数据盘的IO会被强制断掉。|


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
