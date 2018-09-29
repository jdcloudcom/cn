# createContainers


## 描述
创建一台或多台指定配置容器。
- 创建容器需要通过实名认证
- 镜像
    - 容器的镜像通过镜像名称来确定
    - nginx:tag 或 mysql/mysql-server:tag 这样命名的镜像表示 docker hub 官方镜像
    - container-registry/image:tag 这样命名的镜像表示私有仓储的镜像
    - 私有仓储必须兼容 docker registry 认证机制，并通过 secret 来保存机密信息
- hostname 规范
    - 支持两种方式：以标签方式书写或以完整主机名方式书写
    - 标签规范
        - 0-9，a-z(不分大小写)和 -（减号），其他的都是无效的字符串
        - 不能以减号开始，也不能以减号结尾
        - 最小1个字符，最大63个字符
    - 完整的主机名由一系列标签与点连接组成
        - 标签与标签之间使用“.”(点)进行连接
        - 不能以“.”(点)开始，也不能以“.”(点)结尾
        - 整个主机名（包括标签以及分隔点“.”）最多有63个ASCII字符
- 网络配置
    - 指定主网卡配置信息
        - 必须指定一个子网
        - 一台云主机创建时必须指定一个安全组，至多指定 5 个安全组
        - 可以指定 elasticIp 规格来约束创建的弹性 IP，带宽取值范围 [1-200]Mbps，步进 1Mbps
        - 可以指定网卡的主 IP(primaryIpAddress)，该 IP 需要在子网 IP 范围内且未被占用，指定子网 IP 时 maxCount 只能为1
        - 安全组 securityGroup 需与子网 Subnet 在同一个私有网络 VPC 内
        - 主网卡 deviceIndex 设置为 1
- 存储
    - volume 分为 root volume 和 data volume，root volume 的挂载目录是 /，data volume 的挂载目录可以随意指定
    - volume 的底层存储介质当前只支持 cloud 类别，也就是云硬盘
    - 系统盘
        - 云硬盘类型可以选择 ssd、premium-hdd
        - 磁盘大小
            - ssd：范围 [10, 100]GB，步长为 10G
            - premium-hdd：范围 [20, 1000]GB，步长为 10G
        - 自动删除
            - 云盘默认跟随容器实例自动删除，如果是包年包月的数据盘或共享型数据盘，此参数不生效
        - 可以选择已存在的云硬盘
    - 数据盘
        - 云硬盘类型可以选择 ssd、premium-hdd
        - 磁盘大小
            - ssd：范围[20,1000]GB，步长为10G
            - premium-hdd：范围[20,3000]GB，步长为10G
        - 自动删除
            - 默认自动删除
        - 可以选择已存在的云硬盘
        - 单个容器最多可以挂载 7 个 data volume
- 计费
  - 弹性IP的计费模式，如果选择按用量类型可以单独设置，其它计费模式都以主机为准
  - 云硬盘的计费模式以主机为准
- 容器日志
    - 默认在本地分配10MB的存储空间，自动 rotate
- 其他
    - 创建完成后，容器状态为running
    - maxCount 为最大努力，不保证一定能达到 maxCount


## 请求方式
POST

## 请求地址
https://nc.jdcloud-api.com/v1/regions/{regionId}/containers

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**containerSpec**|ContainerSpec|False| |创建容器规格|
|**maxCount**|Integer|False| |购买实例数量；取值范围：[1,100]|

### ContainerSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**args**|String[]|False| |容器执行命令的参数，如果不指定默认是docker镜像的CMD|
|**az**|String|True| |容器所属可用区|
|**charge**|ChargeSpec|False| |计费配置；如不指定，默认计费类型是后付费-按使用时常付费|
|**command**|String[]|False| |容器执行命令，如果不指定默认是docker镜像的ENTRYPOINT|
|**dataVolumes**|VolumeMountSpec[]|False| |挂载的数据Volume信息；最多7个|
|**description**|String|False| |容器描述|
|**elasticIp**|ElasticIpSpec|False| |主网卡主IP关联的弹性IP规格|
|**envs**|EnvVar[]|False| |容器执行的环境变量；如果和镜像中的环境变量Key相同，会覆盖镜像中的值；</br> 最大10对|
|**hostAliases**|HostAlias[]|False| |域名和IP映射的信息；</br> 最大10个alias|
|**hostname**|String|False| |主机名，规范请参考说明文档；默认容器ID|
|**image**|String|False| |镜像名称 </br> 1. Docker Hub官方镜像通过类似nginx, mysql/mysql-server的名字指定 </br> </br> repository长度最大256个字符，tag最大128个字符，registry最大255个字符 </br> 下载镜像超时时间：10分钟|
|**instanceType**|String|True| |实例类型；参考[文档](https://www.jdcloud.com/help/detail/1992/isCatalog/1)|
|**logConfiguration**|LogConfiguration|False| |容器日志配置信息；默认会在本地分配10MB的存储空间|
|**name**|String|True| |容器名称|
|**primaryNetworkInterface**|ContainerNetworkInterfaceAttachmentSpec|True| |主网卡配置信息|
|**rootVolume**|VolumeMountSpec|True| |根Volume信息|
|**secret**|String|False| |secret引用名称；使用Docker Hub和京东云CR的镜像不需要secret|
|**tty**|Boolean|False| |容器是否分配tty。默认不分配|
|**workingDir**|String|False| |容器的工作目录。如果不指定，默认是根目录（/）；必须是绝对路径|
### ChargeSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeDuration**|Integer|False| |预付费计费时长，预付费必填，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration.请参阅具体产品线帮助文档确认该产品线支持的计费类型|
|**chargeUnit**|String|False| |预付费计费单位，预付费必填，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|
### VolumeMountSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**autoDelete**|Boolean|False| |自动删除，删除容器时自动删除此volume，默认为True；只支持磁盘是云硬盘的场景|
|**category**|String|True| |磁盘分类 cloud： 基于云硬盘的卷 root volume只能是cloud类型|
|**cloudDiskId**|String|False| |云硬盘ID；如果使用已有的云硬盘，必须指定partion和fsType|
|**cloudDiskSpec**|DiskSpec|False| |云硬盘规格；随容器自动创建的云硬盘，不会对磁盘分区，只会格式化文件系统|
|**formatVolume**|Boolean|False| |随容器自动创建的新盘，会自动格式化成指定的文件系统类型；挂载已有的盘，默认不会格式化，只会按照指定的fsType去挂载；如果希望格式化，必须设置此字段为true|
|**fsType**|String|False| |指定volume文件系统类型，目前支持[xfs, ext4]；如果新创建的盘，不指定文件系统类型默认格式化成xfs|
|**mountPath**|String|False| |容器内的挂载目录；root volume不需要指定，挂载目录是（/）；data volume必须指定；必须是绝对路径，不能包含(:)|
|**readOnly**|Boolean|False| |只读，默认false；只针对data volume有效；root volume为false，也就是可读可写|
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
|**bandwidthMbps**|Integer|False| |弹性公网IP的限速 单位：MB|
|**chargeSpec**|ChargeSpec|False| |计费配置|
|**provider**|String|False| |IP服务商，取值为bgp或no_bg|
### EnvVar
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |环境变量名称|
|**value**|String|False| |环境变量的值|
### HostAlias
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**hostnames**|String[]|True| |域名列表|
|**ip**|String|True| |IP地址|
### LogConfiguration
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**logDriver**|String|False| |日志Driver名称  default：默认在本地分配10MB的存储空间，自动rotate|
|**options**|LogOption|False| |日志Driver的配置选项|
### LogOption
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**key**|String|False| | |
|**value**|String|False| | |
### ContainerNetworkInterfaceAttachmentSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**autoDelete**|Boolean|False| |指明删除容器时是否删除网卡，默认True；当前只能是True|
|**deviceIndex**|Integer|False| |设备Index|
|**networkInterface**|NetworkInterfaceSpec|True| |网卡接口规范|
### NetworkInterfaceSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**az**|String|True| |可用区，用户的默认可用区|
|**description**|String|False| |描述|
|**primaryIpAddress**|String|False| |网卡主IP|
|**sanityCheck**|Boolean|False| |PortSecurity，取值为0或者1，默认为1|
|**secondaryIpAddresses**|String[]|False| |SecondaryIp列表|
|**secondaryIpCount**|Integer|False| |自动分配的SecondaryIp数量|
|**securityGroups**|String[]|False| |安全组ID列表|
|**subnetId**|String|True| |子网ID|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**containerIds**|String[]| |

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
