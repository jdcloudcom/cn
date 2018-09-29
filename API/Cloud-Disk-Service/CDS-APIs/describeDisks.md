# describeDisks


## 描述
-   filters多个过滤条件之间是逻辑与(AND)，每个条件内部的多个取值是逻辑或(OR)


## 请求方式
GET

## 请求地址
https://disk.jdcloud-api.com/v1/regions/{regionId}/disks

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**filters**|Filter[]|False| |diskId - 云硬盘ID，精确匹配，支持多个<br>diskType - 云硬盘类型，精确匹配，支持多个，取值为 ssd 或 premium-hdd<br>instanceId - 云硬盘所挂载主机的ID，精确匹配，支持多个<br>instanceType - 云硬盘所挂载主机的类型，精确匹配，支持多个<br>status - 可用区，精确匹配，支持多个<br>az - 云硬盘状态，精确匹配，支持多个<br>name - 云硬盘名称，模糊匹配，支持单个<br>multiAttach - 云硬盘是否多点挂载，精确匹配，支持单个<br>|
|**pageNumber**|Integer|False|1|页码, 默认为1, 取值范围：[1,∞)|
|**pageSize**|Integer|False|20|分页大小，默认为20，取值范围：[10,100]|
|**tags**|TagFilter[]|False| |Tag筛选条件|

### Filter
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|
### TagFilter
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**key**|String|True| |Tag键|
|**values**|String[]|True| |Tag值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|
|**result**|Result|查询结果集|

### Result
|名称|类型|描述|
|---|---|---|
|**disks**|Disk[]|查询的云硬盘信息详情列表|
|**totalCount**|Integer|查询的云硬盘数目|
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
|**200**|OK|
|**400**|Invalid parameter|
|**500**|Internal server error|
|**401**|Authentication failed|
|**503**|Service unavailable|
