# modifySnpAttribute


## 描述
修改快照的名字或描述信息

## 请求方式
PATCH

## 请求地址
https://disk.jdcloud-api.com/v1/regions/{regionId}/snapshots/{snapshotId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**snapshotId**|String|True| |快照ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**description**|String|False| |快照描述，name和description必须要指定一个|
|**name**|String|False| |快照名称|


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
