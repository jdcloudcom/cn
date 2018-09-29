# deleteSnapshot


## 描述
-   删除单个云硬盘快照:快照状态必须为 available 或 error 状态。
-   快照独立于云硬盘生命周期，删除快照不会对创建快照的云硬盘有任何影响。
-   快照删除后不可恢复，请谨慎操作。


## 请求方式
DELETE

## 请求地址
https://disk.jdcloud-api.com/v1/regions/{regionId}/snapshots/{snapshotId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**snapshotId**|String|True| |快照ID|

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
