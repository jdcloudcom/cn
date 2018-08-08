# createContainers


## 描述
创建一台或多台指定配置的实例

## 请求方式
POST

## 请求地址
https://nc.jdcloud-api.com/v1/regions/{regionId}/containers

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**containerSpec**|[ContainerSpec](##ContainerSpec)|False||创建容器规格|
|**maxCount**|Integer|False||购买实例数量；取值范围：[1,100]|

### <a name="ContainerSpec">ContainerSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**args**|String[]|False||容器执行命令的参数，如果不指定默认是docker镜像的CMD|
|**az**|String|True||容器所属可用区|
|**charge**|[ChargeSpec](##ChargeSpec)|False||计费配置；如不指定，默认计费类型是后付费-按使用时常付费|
|**command**|String[]|False||容器执行命令，如果不指定默认是docker镜像的ENTRYPOINT|
|**dataVolumes**|[VolumeMountSpec[]](##VolumeMountSpec)|False||挂载的数据Volume信息；最多7个|
|**description**|String|False||容器描述|
|**elasticIp**|[ElasticIpSpec](##ElasticIpSpec)|False||主网卡主IP关联的弹性IP规格|
|**envs**|[EnvVar[]](##EnvVar)|False||容器执行的环境变量；如果和镜像中的环境变量Key相同，会覆盖镜像中的值；</br> 最大10对|
|**hostAliases**|[HostAlias[]](##HostAlias)|False||域名和IP映射的信息；</br> 最大10个alias|
|**hostname**|String|False||主机名，规范请参考说明文档；默认容器ID|
|**image**|String|False||镜像名称 </br> 1. Docker Hub官方镜像通过类似nginx, mysql/mysql-server的名字指定 </br> </br> repository长度最大256个字符，tag最大128个字符，registry最大255个字符 </br> 下载镜像超时时间：10分钟|
|**instanceType**|String|True||实例类型；参考[文档](https://www.jdcloud.com/help/detail/1992/isCatalog/1)|
|**logConfiguration**|[LogConfiguration](##LogConfiguration)|False||容器日志配置信息；默认会在本地分配10MB的存储空间|
|**name**|String|True||容器名称|
|**primaryNetworkInterface**|[ContainerNetworkInterfaceAttachmentSpec](##ContainerNetworkInterfaceAttachmentSpec)|True||主网卡配置信息|
|**rootVolume**|[VolumeMountSpec](##VolumeMountSpec)|True||根Volume信息|
|**secret**|String|False||secret引用名称；使用Docker Hub和京东云CR的镜像不需要secret|
|**tty**|Boolean|False||容器是否分配tty。默认不分配|
|**workingDir**|String|False||容器的工作目录。如果不指定，默认是根目录（/）；必须是绝对路径|
### <a name="ChargeSpec">ChargeSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeDuration**|Integer|False||预付费计费时长，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration|
|**chargeUnit**|String|False||预付费计费单位，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|
### <a name="VolumeMountSpec">VolumeMountSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**autoDelete**|Boolean|False||自动删除，删除容器时自动删除此volume，默认为True；只支持磁盘是云硬盘的场景|
|**category**|String|True||磁盘分类 cloud： 基于云硬盘的卷 root volume只能是cloud类型|
|**cloudDiskId**|String|False||云硬盘ID；如果使用已有的云硬盘，必须指定partion和fsType|
|**cloudDiskSpec**|[DiskSpec](##DiskSpec)|False||云硬盘规格；随容器自动创建的云硬盘，不会对磁盘分区，只会格式化文件系统|
|**formatVolume**|Boolean|False||随容器自动创建的新盘，会自动格式化成指定的文件系统类型；挂载已有的盘，默认不会格式化，只会按照指定的fsType去挂载；如果希望格式化，必须设置此字段为true|
|**fsType**|String|False||指定volume文件系统类型，目前支持[xfs, ext4]；如果新创建的盘，不指定文件系统类型默认格式化成xfs|
|**mountPath**|String|False||容器内的挂载目录；root volume不需要指定，挂载目录是（/）；data volume必须指定；必须是绝对路径，不能包含(:)|
|**readOnly**|Boolean|False||只读，默认false；只针对data volume有效；root volume为false，也就是可读可写|
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
### <a name="ElasticIpSpec">ElasticIpSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**bandwidthMbps**|Integer|False||弹性公网IP的限速 单位：MB|
|**chargeSpec**|[ChargeSpec](##ChargeSpec)|False||计费配置|
|**provider**|String|False||IP服务商，取值为bgp或no_bg|
### <a name="EnvVar">EnvVar</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True||环境变量名称|
|**value**|String|False||环境变量的值|
### <a name="HostAlias">HostAlias</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**hostnames**|String[]|True||域名列表|
|**ip**|String|True||IP地址|
### <a name="LogConfiguration">LogConfiguration</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**logDriver**|String|False||日志Driver名称  default：默认在本地分配10MB的存储空间，自动rotate|
|**options**|[LogOption](##LogOption)|False||日志Driver的配置选项|
### <a name="LogOption">LogOption</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**key**|String|False|||
|**value**|String|False|||
### <a name="ContainerNetworkInterfaceAttachmentSpec">ContainerNetworkInterfaceAttachmentSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**autoDelete**|Boolean|False||指明删除容器时是否删除网卡，默认True；当前只能是True|
|**deviceIndex**|Integer|False||设备Index|
|**networkInterface**|[NetworkInterfaceSpec](##NetworkInterfaceSpec)|True||网卡接口规范|
### <a name="NetworkInterfaceSpec">NetworkInterfaceSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**az**|String|True||可用区，用户的默认可用区|
|**description**|String|False||描述|
|**primaryIpAddress**|String|False||网卡主IP|
|**sanityCheck**|Boolean|False||PortSecurity，取值为0或者1，默认为1|
|**secondaryIpAddresses**|String[]|False||SecondaryIp列表|
|**secondaryIpCount**|Integer|False||自动分配的SecondaryIp数量|
|**securityGroups**|String[]|False||安全组ID列表|
|**subnetId**|String|True||子网ID|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**containerIds**|String[]||

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
