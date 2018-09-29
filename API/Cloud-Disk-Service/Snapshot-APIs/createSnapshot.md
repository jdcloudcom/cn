# createSnapshot


## 描述
-   为指定云硬盘创建快照,新生成的快照的状态为creating。
-   同一地域下单用户快照的配额为15块。
-   为保证数据完整性，请您在创建快照之前，停止对云硬盘进行写入操作，以保证快照数据的完整性。
-   在执行创建快照前，建议您对云硬盘进行卸载操作，创建快照后再重新挂载到云主机上。
-   手动快照的生命周期独立于云硬盘，请您及时删除不需要的快照。
-   创建快照所需时间取决于云硬盘容量的大小，云硬盘容量越大耗时越长。


## 请求方式
POST

## 请求地址
https://disk.jdcloud-api.com/v1/regions/{regionId}/snapshots

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clientToken**|String|True| |幂等性校验参数|
|**snapshotSpec**|SnapshotSpec|True| |创建快照规格|

### SnapshotSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**description**|String|False| |快照描述|
|**diskId**|String|True| |用于创建快照的云盘ID|
|**name**|String|True| |快照名称|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|
|**result**|Result|结果集|

### Result
|名称|类型|描述|
|---|---|---|
|**snapshotId**|String|创建的快照ID|

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**500**|Internal server error|
|**503**|Service unavailable|
|**200**|OK|
|**404**|Not found|
|**429**|Quota exceeded|
