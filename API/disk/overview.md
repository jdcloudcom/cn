# 云硬盘API


## 简介
云硬盘API包含云硬盘相关接口和快照相关接口。可提供批量创建云硬盘，删除云硬盘，制作云硬盘快照等功能。


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**createDisks**|POST|创建一块或多块云硬盘|
|**createSnapshot**|POST|为指定云硬盘创建快照,新生成的快照的状态为creating|
|**deleteDisk**|DELETE|删除单个云硬盘|
|**deleteSnapshot**|DELETE|删除单个云硬盘快照:快照状态必须为 available 或 error 状态|
|**describeDisk**|GET|查询云硬盘信息详情|
|**describeDisks**|GET|查询云硬盘列表|
|**describeSnapshot**|GET|查询云硬盘快照信息详情|
|**describeSnapshots**|GET|查询云硬盘快照列表|
|**extendDisk**|POST|扩容云硬盘到指定大小|
|**modifyDiskAttribute**|PATCH|修改云硬盘的名字或描述信息|
|**modifySnpAttribute**|PATCH|修改快照的名字或描述信息|
|**restoreDisk**|POST|从已有快照恢复一块云硬盘|
