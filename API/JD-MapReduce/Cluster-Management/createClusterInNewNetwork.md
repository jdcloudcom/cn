# createClusterInNewNetwork


## 描述
创建新集群

## 请求方式
POST

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/cluster:create

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clusterModel**|ClusterModel|True| | |

### ClusterModel
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**bandwidth**|Integer|False|5|网络带宽上限|
|**coreInstanceType**|String|False| |Core节点规格，比如：g.n1.xlarge，更多规格请参考[文档](https://www.jdcloud.com/help/detail/296/isCatalog/1)|
|**dataCenter**|String|False|cn-north-1|地域，同regionID|
|**haFlag**|Boolean|False|True|集群是否为高可用模式|
|**jssFlag**|Boolean|False| |是否关联对象存储|
|**masterInstanceType**|String|False| |Master节点规格，比如：g.n1.xlarge，更多规格请参考[文档](https://www.jdcloud.com/help/detail/296/isCatalog/1)|
|**masterNodeDiskType**|String|False| |"Master节点云盘类型，可传类型为（以下以“/”分割各类型）"<br>"NBD/NBD_SATA"<br>"分别代表：性能型/容量型"<br>|
|**masterNodeDiskVolume**|Integer|False| |Master节点云盘容量，必须是10的整数倍，且大于20小于3000|
|**masterNodeNumber**|Integer|False| |Master节点数量|
|**name**|String|False| |集群名称，长度为6到32个字符，支持中文、数字、大小写字母、英文下划线“_”及中划线“-”|
|**password**|String|False| |"集群密码"<br>"1.必须包含大写字母、小写字母、数字及特殊字符中三类，且不能少于8字符不能超过30字符"<br>"2.特殊字符如下!@#$%^*"<br>"3.不能出现的字符或完整单词，如下：jd、JD、360、bug、BUG、com、COM、jcloud、JCLOUD、cloud、CLOUD、password、PASSWORD"<br>"4.不能出现连续数字，例：123、987"<br>"5.不能出现连续或键位连续字母，例：abc、CBA、bcde、qaz、tfc、zaq、qwer"<br>"6.密码中不能出现自己的用户名"<br>|
|**payType**|String|False| |"付费类型，请填写以下列表中的一个："<br>"按量"<br>|
|**slaveNodeDiskType**|String|False| |"Slave节点云盘类型，可传类型为（以下以“/”分割各类型）"<br>"NBD/NBD_SATA"<br>"分别代表：性能型/容量型"<br>|
|**slaveNodeDiskVolume**|Integer|False| |Slave节点云盘容量，必须是10的整数倍，且大于20小于3000|
|**slaveNodeNumber**|Integer|False| |Slave节点数量|
|**softwareList**|String|False|HADOOP,ZOOKEEPER|软件清单，不同软件之间以英文逗号(,)分割，参考[文档](https://www.jdcloud.com/help/detail/1323/isCatalog/1)|
|**version**|String|False| |"软件服务版本，请填写以下列表中的一个："<br>"JMR1.0.0"<br>"JMR1.0.1"<br>"JMR1.0.2"<br>"JMR2.0.0"<br>"JMR_BD-OS-1.0"<br>|
|**vpcId**|String|False|new|私有网络ID|
|**vpcSubnetId**|String|False|new|子网UUID，可以通过查询子网列表获得|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**message**|String| |
|**status**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
