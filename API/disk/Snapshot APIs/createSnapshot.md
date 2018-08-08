# createSnapshot


## 描述
为指定云硬盘创建快照,新生成的快照的状态为creating

## 请求方式
POST

## 请求地址
https://disk.jdcloud-api.com/v1/regions/{regionId}/snapshots

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clientToken**|String|True||幂等性校验参数|
|**snapshotSpec**|[SnapshotSpec](##SnapshotSpec)|True||创建快照规格|

### <a name="SnapshotSpec">SnapshotSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**description**|String|False||快照描述|
|**diskId**|String|True||用于创建快照的云盘ID|
|**name**|String|True||快照名称|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|
|**result**|[Result](##Result)|结果集|


### <a name="Result">Result</a>
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

## 请求示例
POST
```

```

## 返回示例
无
