# createDisks


## 描述
创建一块或多块云硬盘

## 请求方式
POST

## 请求地址
https://disk.jdcloud-api.com/v1/regions/{regionId}/disks

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clientToken**|String|True||幂等性校验参数|
|**diskSpec**|[DiskSpec](##DiskSpec)|True||创建云硬盘规格|
|**maxCount**|Integer|True||购买实例数量；取值范围：[1,100]|

### <a name="DiskSpec">DiskSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**az**|String|True||云硬盘所属的可用区|
|**charge**|[ChargeSpec](##ChargeSpec)|False||计费配置；如不指定，默认计费类型是后付费-按使用时常付费|
|**description**|String|False||云硬盘描述|
|**diskSizeGB**|Integer|True||云硬盘大小，单位为 GiB，ssd 类型取值范围[20,1000]GB，步长为10G，premium-hdd 类型取值范围[20,3000]GB，步长为10G|
|**diskType**|String|True||云硬盘类型，取值为ssd、premium-hdd之一|
|**name**|String|True||云硬盘名称|
|**snapshotId**|String|False||用于创建云硬盘的快照ID|
### <a name="ChargeSpec">ChargeSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeDuration**|Integer|False||预付费计费时长，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration|
|**chargeUnit**|String|False||预付费计费单位，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|
|**result**|[Result](##Result)|结果集|


### <a name="Result">Result</a>
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

## 请求示例
POST
```

```

## 返回示例
无
