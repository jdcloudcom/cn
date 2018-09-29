# deleteDisk


## 描述
-   删除一块按配置计费的云硬盘，磁盘类型包括高效云盘和SSD云盘。
-   硬盘被删除后，云硬盘快照可以被保留。
-   释放磁盘时，云盘的状态必须为 待挂载（Available）。
-   如果指定 ID 的磁盘不存在，请求将被忽略。


## 请求方式
DELETE

## 请求地址
https://disk.jdcloud-api.com/v1/regions/{regionId}/disks/{diskId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**diskId**|String|True| |云硬盘ID|
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
