# deleteInstance


## 描述
删除按配置计费、或包年包月已到期的单个云主机。不能删除没有计费信息的云主机。<br>
云主机状态必须为运行<b>running</b>、停止<b>stopped</b>、错误<b>error</b>，同时云主机没有正在进行中的任务才可删除。<br>
包年包月未到期的云主机不能删除。<br>
如果主机中挂载的数据盘为按配置计费的云硬盘，并且不是共享型云硬盘，并且AutoDelete属性为true，那么数据盘会随主机一起删除。
</br>敏感操作，可开启<a href="https://docs.jdcloud.com/IAM/Operation-Protection">MFA操作保护</a>

## 请求方式
DELETE

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |云主机ID|
|**regionId**|String|True| |地域ID|

## 请求参数
无


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
