# operateMonitor


## 描述
监控项的操作集合，包括：删除，暂停，启动, 手动恢复, 手动切换

## 请求方式
POST

## 请求地址
https://clouddnsservice.jdcloud-api.com/v1/regions/{regionId}/domain/{domainId}/monitorOperate

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainId**|String|True| |域名ID|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**action**|String|True| |删除del, 暂停stop, 开启start, 手动恢复recover，手动切换switch|
|**ids**|Integer[]|True| |监控项ID|
|**switchTarget**|String|False| |监控项的主机值, 手动切换时必填|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|此次请求的ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
