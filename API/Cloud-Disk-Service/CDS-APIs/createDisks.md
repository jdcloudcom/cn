# createDisks


## 描述
-   创建一块或多块按配置或者按使用时长付费的云硬盘。
-   磁盘类型包括高效云盘和SSD云盘。
-   计费方式默认为按配置付费。
-   创建完成后，云硬盘状态为 available。
-   可选参数快照 ID用于从快照创建新盘。
-   批量创建时，云硬盘的命名为 硬盘名称-数字，例如 myDisk-1，myDisk-2。
-   maxCount为最大努力，不保证一定能达到maxCount。


## 请求方式
POST

## 请求地址
https://disk.jdcloud-api.com/v1/regions/{regionId}/disks

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clientToken**|String|True| |幂等性校验参数|
|**diskSpec**|DiskSpec|True| |创建云硬盘规格|
|**maxCount**|Integer|True| |购买实例数量；取值范围：[1,100]|

### DiskSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**az**|String|True| |云硬盘所属的可用区|
|**charge**|ChargeSpec|False| |计费配置；如不指定，默认计费类型是后付费-按使用时常付费|
|**description**|String|False| |云硬盘描述|
|**diskSizeGB**|Integer|True| |云硬盘大小，单位为 GiB，ssd 类型取值范围[20,1000]GB，步长为10G，premium-hdd 类型取值范围[20,3000]GB，步长为10G|
|**diskType**|String|True| |云硬盘类型，取值为ssd、premium-hdd之一|
|**multiAttachable**|Boolean|False| |云硬盘是否支持一盘多主机挂载，默认为false（不支持）|
|**name**|String|True| |云硬盘名称|
|**snapshotId**|String|False| |用于创建云硬盘的快照ID|
### ChargeSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeDuration**|Integer|False| |预付费计费时长，预付费必填，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration.请参阅具体产品线帮助文档确认该产品线支持的计费类型|
|**chargeUnit**|String|False| |预付费计费单位，预付费必填，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|
|**result**|Result|结果集|

### Result
|名称|类型|描述|
|---|---|---|
|**diskIds**|String[]|创建的云硬盘ID列表|

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
