# calculateClusterPrice


## 描述
计算对应规格属性的集群价格

## 请求方式
POST

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/cluster:calculate

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clusterListViewModel**|ClusterListViewModel|True| |集群信息视图，除userName、dataCenter外均需要传入|

### ClusterListViewModel
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**bandwidthOut**|Integer|False| |网络带宽|
|**coreInstanceType**|String|False| |核心实例类型|
|**dataCenter**|String|False| |数据中心位置|
|**masterInstanceType**|String|False| |主节点实例类型|
|**masterNodeDiskType**|String|False| |主节点磁盘类型|
|**masterNodeDiskVolume**|Integer|False| |主节点磁盘容量|
|**masterNodeInfo**|String|False| |主节点信息|
|**masterNodeNumber**|Integer|False| |主节点数量|
|**slaveNodeDiskType**|String|False| |从节点磁盘类型|
|**slaveNodeDiskVolume**|Integer|False| |从节点磁盘容量|
|**slaveNodeInfo**|String|False| |从节点信息|
|**slaveNodeNumber**|Integer|False| |从节点数量|
|**userName**|String|False| |用户名|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|Integer| |
|**message**|String| |
|**status**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
