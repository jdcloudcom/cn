# attachDisk


## 描述
为一台云主机挂载一块数据盘(云硬盘)，云主机和云硬盘没有正在进行中的的任务时才可挂载。<br>
云主机状态必须是<b>running</b>或<b>stopped</b>状态。<br>
本地盘(local类型)做系统盘的云主机可挂载8块数据盘，云硬盘(cloud类型)做系统盘的云主机可挂载7块数据盘。


## 请求方式
POST

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:attachDisk

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |云主机ID|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**autoDelete**|Boolean|False| |自动随主机删除此云硬盘，默认为False。仅按配置计费云硬盘支持修改此参数，包年包月云硬盘默认为False且不可修改。如果是共享型云硬盘，此参数无效。|
|**deviceName**|String|False| |数据盘的逻辑挂载点[vda,vdb,vdc,vdd,vde,vdf,vdg,vdh,vdi]，挂载系统盘时vda必传|
|**diskId**|String|True| |云硬盘ID|


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
