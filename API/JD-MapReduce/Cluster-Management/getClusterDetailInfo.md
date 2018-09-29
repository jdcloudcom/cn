# getClusterDetailInfo


## 描述
集群扩容时，显示集群详情

## 请求方式
POST

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/clusterInfo/{clusterId}:detail

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clusterId**|String|True| |需要扩容的集群ID|
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
|**data**|ClusterDetailInfo| |
|**message**|String| |
|**status**|String| |
### ClusterDetailInfo
|名称|类型|描述|
|---|---|---|
|**masterCore**|Integer|Master节点CPU|
|**masterDiskType**|String|"Master节点云盘类型，可传类型为（以下以“/”分割各类型）"<br>"NBD/NBD_SATA"<br>"分别代表：性能型/容量型"<br>|
|**masterDiskVolume**|Integer|Master节点云盘容量，必须是10的整数倍，且大于20小于3000|
|**masterInstanceInfo**|String|master节点实例信息|
|**masterInstanceType**|String|Master节点规格，比如：g.n1.xlarge，更多规格请参考[文档](https://www.jdcloud.com/help/detail/296/isCatalog/1)|
|**masterMemory**|Integer|Master节点内存（推荐至少8G内存，否则服务可能会部署失败）|
|**materNum**|Integer|Master节点数量|
|**slaveCore**|Integer|Slave节点CPU|
|**slaveDiskType**|String|"Slave节点云盘类型，可传类型为（以下以“/”分割各类型）"<br>"NBD/NBD_SATA"<br>"分别代表：性能型/容量型"<br>|
|**slaveDiskVolume**|Integer|Slave节点云盘容量，必须是10的整数倍，且大于20小于3000|
|**slaveInstanceInfo**|String|Slave节点实例信息|
|**slaveInstanceType**|String|Slave节点规格，比如：g.n1.xlarge，更多规格请参考[文档](https://www.jdcloud.com/help/detail/296/isCatalog/1)|
|**slaveMemory**|Integer|Slave节点内存(推荐至少4G内存，否则服务可能会部署失败)|
|**slaveNum**|Integer|Slave节点数量|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
