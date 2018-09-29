# stopContainer


## 描述
停止处于运行状态的单个实例，处于任务执行中的容器无法启动。


## 请求方式
POST

## 请求地址
https://nc.jdcloud-api.com/v1/regions/{regionId}/containers/{containerId}:stopContainer

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**containerId**|String|True| |Container ID|
|**regionId**|String|True| |Region ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
