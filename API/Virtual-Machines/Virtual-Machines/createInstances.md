# createInstances


## 描述
创建一台或多台指定配置的云主机，创建模式分为三种：1.普通方式、2.使用高可用组、3.使用启动模板。三种方式创建云主机时参数的必传与非必传是不同的，具体请参考<a href="http://docs.jdcloud.com/virtual-machines/api/create_vm_sample">参数详细说明</a><br>
- 创建云主机需要通过实名认证
- 实例规格
    - 可查询<a href="http://docs.jdcloud.com/virtual-machines/api/describeinstancetypes">DescribeInstanceTypes</a>接口获得指定地域或可用区的规格信息。
    - 不能使用已下线、或已售馨的规格ID
- 镜像
    - Windows Server 2012 R2标准版 64位 中文版 SQL Server 2014 标准版 SP2内存需大于1GB；
    - Windows Server所有镜像CPU不可选超过64核CPU。
    - 可查询<a href="http://docs.jdcloud.com/virtual-machines/api/describeimages">DescribeImages</a>接口获得指定地域的镜像信息。
    - 选择的镜像必须支持选择的实例规格。可查询<a href="http://docs.jdcloud.com/virtual-machines/api/describeimageconstraints">DescribeImageConstraints</a>接口获得指定镜像的实例规格限制信息。<br>
- 网络配置
    - 指定主网卡配置信息
        - 必须指定subnetId
        - 可以指定elasticIp规格来约束创建的弹性IP，带宽取值范围[1-100]Mbps，步进1Mbps
        - 可以指定主网卡的内网主IP(primaryIpAddress)，此时maxCount只能为1
        - 安全组securityGroup需与子网Subnet在同一个私有网络VPC内
        - 一台云主机创建时必须指定一个安全组，至多指定5个安全组，如果没有指定安全组，默认使用默认安全组
        - 主网卡deviceIndex设置为1
- 存储
    - 系统盘
        - 磁盘分类，系统盘支持local或cloud
        - 磁盘大小
            - local：不能指定大小，默认为40GB
            - cloud：取值范围: 40-500GB，并且不能小于镜像的最小系统盘大小，如果没有指定，默认以镜像中的系统盘大小为准
        - 自动删除
            - 如果是local，默认自动删除，不能修改此属性
            - 如果是cloud类型的按配置计费的云硬盘，可以指定为True
    - 数据盘
        - 磁盘分类，数据盘仅支持cloud
        - 云硬盘类型可以选择ssd、premium-hdd
        - 磁盘大小
            - premium-hdd：范围[20,3000]GB，步长为10G
            - ssd：范围[20,1000]GB，步长为10G
        - 自动删除
            - 默认自动删除，如果是包年包月的数据盘或共享型数据盘，此参数不生效
            - 可以指定SnapshotId创建云硬盘
        - 可以从快照创建磁盘
    - local类型系统的云主机可以挂载8块云硬盘
    - cloud类型系统的云主机可以挂载7块云硬盘
- 计费
    - 弹性IP的计费模式，如果选择按用量类型可以单独设置，其它计费模式都以主机为准
    - 云硬盘的计费模式以主机为准
- 其他
    - 创建完成后，主机状态为running
    - 仅Linux系统云主机可以指定密钥
    - maxCount为最大努力，不保证一定能达到maxCount
    - 虚机的az会覆盖磁盘的az属性
- 密码
    - <a href="http://docs.jdcloud.com/virtual-machines/api/general_parameters">参考公共参数规范</a>


## 请求方式
POST

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/instances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clientToken**|String|False| |用于保证请求的幂等性。由客户端生成，长度不能超过64个字符。<br>|
|**instanceSpec**|InstanceSpec|True| |描述云主机配置<br>|
|**maxCount**|Integer|False|1|购买云主机的数量；取值范围：[1,100]，默认为1。<br>|

### InstanceSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**agId**|String|False| |高可用组Id。指定了此参数后，只能通过高可用组关联的实例模板创建虚机，并且实例模板中的参数不可覆盖替换。实例模板以外的参数还可以指定。|
|**az**|String|False| |云主机所属的可用区。|
|**charge**|ChargeSpec|False| |计费配置<br>云主机不支持按用量方式计费，默认为按配置计费。<br>打包创建数据盘的情况下，数据盘的计费方式只能与云主机保持一致。<br>打包创建弹性公网IP的情况下，若公网IP的计费方式没有指定为按用量计费，那么公网IP计费方式只能与云主机保持一致。<br>|
|**dataDisks**|InstanceDiskAttachmentSpec[]|False| |数据盘配置信息，本地盘(local类型)做系统盘的云主机可挂载8块数据盘，云硬盘(cloud类型)做系统盘的云主机可挂载7块数据盘。|
|**description**|String|False| |主机描述，<a href="http://docs.jdcloud.com/virtual-machines/api/general_parameters">参考公共参数规范</a>。|
|**elasticIp**|ElasticIpSpec|False| |主网卡主IP关联的弹性IP规格|
|**imageId**|String|False| |镜像ID。可查询<a href="http://docs.jdcloud.com/virtual-machines/api/describeimages">DescribeImages</a>接口获得指定地域的镜像信息。|
|**instanceTemplateId**|String|False| |实例模板id，如果没有使用高可用组，那么对于实例模板中没有的信息，需要使用创建虚机的参数进行补充，或者选择覆盖启动模板中的参数。|
|**instanceType**|String|False| |实例规格。可查询<a href="http://docs.jdcloud.com/virtual-machines/api/describeinstancetypes">DescribeInstanceTypes</a>接口获得指定地域或可用区的规格信息。|
|**keyNames**|String[]|False| |密钥对名称，当前只支持传入一个。|
|**name**|String|True| |云主机名称，<a href="http://docs.jdcloud.com/virtual-machines/api/general_parameters">参考公共参数规范</a>。|
|**password**|String|False| |密码，<a href="http://docs.jdcloud.com/virtual-machines/api/general_parameters">参考公共参数规范</a>。|
|**primaryNetworkInterface**|InstanceNetworkInterfaceAttachmentSpec|False| |主网卡配置信息|
|**systemDisk**|InstanceDiskAttachmentSpec|False| |系统盘配置信息|
### ChargeSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeDuration**|Integer|False| |预付费计费时长，预付费必填，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration.请参阅具体产品线帮助文档确认该产品线支持的计费类型|
|**chargeUnit**|String|False| |预付费计费单位，预付费必填，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|
### InstanceDiskAttachmentSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**autoDelete**|Boolean|False| |是否随云主机一起删除，即删除主机时是否自动删除此磁盘，默认为true，本地盘(local)不能更改此值。<br>如果云主机中的数据盘(cloud)是包年包月计费方式，此参数不生效。<br>如果云主机中的数据盘(cloud)是共享型数据盘，此参数不生效。<br>|
|**cloudDiskSpec**|DiskSpec|False| |数据盘配置|
|**deviceName**|String|False| |数据盘逻辑挂载点，取值范围：vda,vdb,vdc,vdd,vde,vdf,vdg,vdh,vdi|
|**diskCategory**|String|False| |磁盘分类，取值为本地盘(local)或者云硬盘(cloud)。<br>系统盘支持本地盘(local)或者云硬盘(cloud)。系统盘选择local类型，必须使用localDisk类型的镜像；同理系统盘选择cloud类型，必须使用cloudDisk类型的镜像。<br>数据盘仅支持云硬盘(cloud)。<br>|
|**noDevice**|Boolean|False| |排除设备，使用此参数noDevice配合deviceName一起使用。<br>创建整机镜像：如deviceName:vdb、noDevice:true，则表示云主机中的数据盘vdb不参与创建镜像。<br>创建模板：如deviceName:vdb、noDevice:true，则表示镜像中的数据盘vdb不参与创建主机。<br>创建主机：如deviceName:vdb、noDevice:true，则表示镜像中的数据盘vdb，或者模板(使用模板创建主机)中的数据盘vdb不参与创建主机。<br>|
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
### ElasticIpSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**bandwidthMbps**|Integer|True| |弹性公网IP的限速（单位：Mbps），取值范围为[1-200]|
|**chargeSpec**|ChargeSpec|False| |计费配置|
|**provider**|String|True| |IP服务商，取值为bgp或no_bgp，cn-north-1：bgp；cn-south-1：[bgp，no_bgp]；cn-east-1：[bgp，no_bgp]；cn-east-2：bgp|
### InstanceNetworkInterfaceAttachmentSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**deviceIndex**|Integer|False| |网卡设备Index，主网卡只能是1|
|**networkInterface**|NetworkInterfaceSpec|False| |网卡接口规范|
### NetworkInterfaceSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**az**|String|False| |可用区，用户的默认可用区|
|**description**|String|False| |描述,​ 允许输入UTF-8编码下的全部字符，不超过256字符|
|**networkInterfaceName**|String|False| |网卡名称，只允许输入中文、数字、大小写字母、英文下划线“_”及中划线“-”，不允许为空且不超过32字符。|
|**primaryIpAddress**|String|False| |网卡主IP，如果不指定，会自动从子网中分配|
|**sanityCheck**|Integer|False| |源和目标IP地址校验，取值为0或者1,默认为1|
|**secondaryIpAddresses**|String[]|False| |SecondaryIp列表|
|**secondaryIpCount**|Integer|False| |自动分配的SecondaryIp数量|
|**securityGroups**|String[]|False| |要绑定的安全组ID列表，最多指定5个安全组|
|**subnetId**|String|True| |子网ID|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**instanceIds**|String[]| |

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
