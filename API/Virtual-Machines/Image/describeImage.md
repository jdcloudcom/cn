# describeImage


## 描述
查询镜像详情。


## 请求方式
GET

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/images/{imageId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**imageId**|String|True| |镜像ID|
|**regionId**|String|True| |地域ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**image**|Image|镜像详情|
### Image
|名称|类型|描述|
|---|---|---|
|**architecture**|String|镜像架构。取值：i386,x86_64|
|**createTime**|String|创建时间|
|**dataDisks**|InstanceDiskAttachment[]|镜像数据盘映射信息|
|**desc**|String|镜像描述|
|**imageId**|String|镜像ID|
|**imageSource**|String|镜像来源。取值：jcloud：官方镜像；marketplace：镜像市场镜像；self：用户自己的镜像；shared：其他用户分享的镜像|
|**name**|String|镜像名称|
|**osType**|String|镜像的操作系统类型。取值：windows,linux|
|**osVersion**|String|镜像的操作系统版本。|
|**platform**|String|镜像的操作系统发行版。取值：Ubuntu,CentOS,Windows Server|
|**progress**|String|镜像复制和转换时的进度，仅显示数值，单位为百分比|
|**rootDeviceType**|String|镜像支持的系统盘类型。取值：localDisk：本地盘系统盘；cloudDisk：云盘系统盘。|
|**sizeMB**|Integer|镜像文件实际大小|
|**snapshotId**|String|创建云盘系统盘所使用的云硬盘快照ID。系统盘类型为本地盘的镜像，此参数为空。|
|**status**|String|<a href="http://docs.jdcloud.com/virtual-machines/api/image_status">参考镜像状态</a>|
|**systemDisk**|InstanceDiskAttachment|镜像系统盘配置|
|**systemDiskSizeGB**|Integer|镜像系统盘大小|
### InstanceDiskAttachment
|名称|类型|描述|
|---|---|---|
|**autoDelete**|Boolean|随云主机一起删除，删除主机时自动删除此磁盘，默认为true，本地盘(local)不能更改此值。<br>如果云主机中的数据盘(cloud)是包年包月计费方式，此参数不生效。<br>如果云主机中的数据盘(cloud)是共享型数据盘，此参数不生效。<br>|
|**cloudDisk**|Disk|云硬盘配置|
|**deviceName**|String|数据盘逻辑挂载点，取值范围：vda,vdb,vdc,vdd,vde,vdf,vdg,vdh,vdi|
|**diskCategory**|String|磁盘分类，取值为本地盘(local)或者数据盘(cloud)。<br>系统盘支持本地盘(local)或者云硬盘(cloud)。系统盘选择local类型，必须使用localDisk类型的镜像；同理系统盘选择cloud类型，必须使用cloudDisk类型的镜像。<br>数据盘仅支持云硬盘(cloud)。<br>|
|**localDisk**|LocalDisk|本地磁盘配置|
|**status**|String|数据盘挂载状态，取值范围：attaching,detaching,attached,detached,error_attach,error_detach|
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
### LocalDisk
|名称|类型|描述|
|---|---|---|
|**diskSizeGB**|Integer|磁盘大小|
|**diskType**|String|磁盘类型，取值范围{premium-hdd, ssd}|

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
