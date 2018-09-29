# restoreDisk


## 描述
-   仅可对制作快照的源硬盘进行数据恢复操作。
-   仅源硬盘处于可用状态时才能使用快照进行数据恢复操作。
-   云硬盘恢复后，当前数据将被清除，请您谨慎操作。


## 请求方式
POST

## 请求地址
https://disk.jdcloud-api.com/v1/regions/{regionId}/disks/{diskId}:restore

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**diskId**|String|True| |云硬盘ID|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**snapshotId**|String|True| |用于恢复云盘的快照ID|


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
