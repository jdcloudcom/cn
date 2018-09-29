# describeDisk


## 描述
查询某一块云硬盘的信息详情

## 请求方式
GET

## 请求地址
https://disk.jdcloud-api.com/v1/regions/{regionId}/disks/{diskId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**diskId**|String|True| |云硬盘ID|
|**regionId**|String|True| |地域ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|
|**result**|Result|查询的云硬盘信息详情|

### Result
|名称|类型|描述|
|---|---|---|
|**disk**|Disk| |
### Disk
|名称|类型|描述|
|---|---|---|
|**attachments**|DiskAttachment[]|挂载信息|
|**az**|String|云硬盘所属AZ|
|**charge**|Charge|云硬盘计费配置信息|
|**createTime**|String|创建云硬盘时间|
|**description**|String|云硬盘描述，允许输入UTF-8编码下的全部字符，不超过256字符。|
|**diskId**|String|云硬盘ID|
|**diskSizeGB**|Integer|磁盘大小，单位为 GiB|
|**diskType**|String|磁盘类型，取值为 ssd 或 premium-hdd|
|**multiAttachable**|Boolean|云盘是否支持多挂载|
|**name**|String|云硬盘名称，只允许输入中文、数字、大小写字母、英文下划线“_”及中划线“-”，不允许为空且不超过32字符。|
|**snapshotId**|String|创建该云硬盘的快照ID|
|**status**|String|云硬盘状态，取值为 creating、available、in-use、extending、restoring、deleting、deleted、error_create、error_delete、error_restore、error_extend 之一|
|**tags**|Tag[]|Tag信息|
### DiskAttachment
|名称|类型|描述|
|---|---|---|
|**attachTime**|String|挂载时间|
|**attachmentId**|String|挂载ID|
|**diskId**|String|云硬盘ID|
|**instanceId**|String|挂载实例的ID|
|**instanceType**|String|挂载实例的类型，取值为 vm、nc|
|**status**|String|挂载状态，取值为 "attaching", "attached", "detaching", "detached"|
### Charge
|名称|类型|描述|
|---|---|---|
|**chargeExpiredTime**|String|过期时间，预付费资源的到期时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ，后付费资源此字段内容为空|
|**chargeMode**|String|支付模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration|
|**chargeRetireTime**|String|预期释放时间，资源的预期释放时间，预付费/后付费资源均有此值，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeStartTime**|String|计费开始时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeStatus**|String|费用支付状态，取值为：normal、overdue、arrear，normal表示正常，overdue表示已到期，arrear表示欠费|
### Tag
|名称|类型|描述|
|---|---|---|
|**key**|String|Tag键|
|**value**|String|Tag值|

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
