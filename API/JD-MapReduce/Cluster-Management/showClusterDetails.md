# showClusterDetails


## 描述
根据clusterId查询对应集群详情

## 请求方式
GET

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/detail

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**id**|String|True| |集群ID；由八位字符组成|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|ClusterDetailModel|对应集群的详细信息|
|**message**|String| |
|**status**|String| |
### ClusterDetailModel
|名称|类型|描述|
|---|---|---|
|**bandwidthOut**|Integer|网络带宽|
|**clusterPrimaryId**|Integer|集群主键ID|
|**createTime**|String|创建时间|
|**dataCenter**|String|地域，同regionID|
|**duration**|String|运营时长|
|**haFlag**|Boolean|是否为高可用模式|
|**hardware**|HardwareInfo[]| |
|**id**|String|集群ID|
|**jssFlag**|Boolean|是否关联对象存储|
|**name**|String|集群名称，长度为6到32个字符，支持中文、数字、大小写字母、英文下划线“_”及中划线“-”|
|**nodeCount**|Integer|节点数量|
|**payPrice**|String|付费价格|
|**payType**|String|付费类型|
|**softwareStack**|Object|软件信息|
|**status**|String|集群状态|
|**vpcName**|String|私有网络名称|
|**vpcSubnetName**|String|子网名称|
### HardwareInfo
|名称|类型|描述|
|---|---|---|
|**firewall**|String|防火墙|
|**innerIp**|String|内网IP|
|**instanceInfo**|String|节点硬件类型|
|**instanceType**|String|节点硬件配置|
|**msg**|String|消息|
|**nodeCoreNum**|Integer|节点核心数|
|**nodeDiskType**|String|节点硬盘类型|
|**nodeDiskVolume**|Integer|节点硬盘容量|
|**nodeMemoryNum**|Integer|节点内存数|
|**nodeName**|String|节点名称|
|**nodeStatus**|String|节点状态|
|**nodeSystemInfo**|String|节点系统信息|
|**nodeType**|String|节点类型|
|**outerIp**|String|外网IP|
|**serverId**|String|节点实例ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
