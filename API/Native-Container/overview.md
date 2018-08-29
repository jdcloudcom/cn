# 原生容器


## 简介
原生容器相关接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**associateElasticIp**|POST|容器绑定弹性公网 IP，绑定的是主网卡、主内网IP对应的弹性IP. <br></br>一台云主机只能绑定一个弹性公网 IP(主网卡)，若主网卡已存在弹性公网IP，会返回错误。<br></br>如果是黑名单中的用户，会返回错误。</br>|
|**createContainers**|POST|创建一台或多台指定配置容器。</br>\- 创建容器需要通过实名认证</br>\- 镜像</br>    \- 容器的镜像通过镜像名称来确定</br>    \- nginx:tag 或 mysql/mysql\-server:tag 这样命名的镜像表示 docker hub 官方镜像</br>    \- container\-registry/image:tag 这样命名的镜像表示私有仓储的镜像</br>    \- 私有仓储必须兼容 docker registry 认证机制，并通过 secret 来保存机密信息</br>\- hostname 规范</br>    \- 支持两种方式：以标签方式书写或以完整主机名方式书写</br>    \- 标签规范</br>        \- 0\-9，a\-z(不分大小写)和 \-（减号），其他的都是无效的字符串</br>        \- 不能以减号开始，也不能以减号结尾</br>        \- 最小1个字符，最大63个字符</br>    \- 完整的主机名由一系列标签与点连接组成</br>        \- 标签与标签之间使用“.”(点)进行连接</br>        \- 不能以“.”(点)开始，也不能以“.”(点)结尾</br>        \- 整个主机名（包括标签以及分隔点“.”）最多有63个ASCII字符</br>\- 网络配置</br>    \- 指定主网卡配置信息</br>        \- 必须指定一个子网</br>        \- 一台云主机创建时必须指定一个安全组，至多指定 5 个安全组</br>        \- 可以指定 elasticIp 规格来约束创建的弹性 IP，带宽取值范围 [1\-200]Mbps，步进 1Mbps</br>        \- 可以指定网卡的主 IP(primaryIpAddress)，该 IP 需要在子网 IP 范围内且未被占用，指定子网 IP 时 maxCount 只能为1</br>        \- 安全组 securityGroup 需与子网 Subnet 在同一个私有网络 VPC 内</br>        \- 主网卡 deviceIndex 设置为 1</br>\- 存储</br>    \- volume 分为 root volume 和 data volume，root volume 的挂载目录是 /，data volume 的挂载目录可以随意指定</br>    \- volume 的底层存储介质当前只支持 cloud 类别，也就是云硬盘</br>    \- 系统盘</br>        \- 云硬盘类型可以选择 ssd、premium\-hdd</br>        \- 磁盘大小</br>            \- ssd：范围 [10, 100]GB，步长为 10G</br>            \- premium\-hdd：范围 [20, 1000]GB，步长为 10G</br>        \- 自动删除</br>            \- 云盘默认跟随容器实例自动删除，如果是包年包月的数据盘或共享型数据盘，此参数不生效</br>        \- 可以选择已存在的云硬盘</br>    \- 数据盘</br>        \- 云硬盘类型可以选择 ssd、premium\-hdd</br>        \- 磁盘大小</br>            \- ssd：范围[20,1000]GB，步长为10G</br>            \- premium\-hdd：范围[20,3000]GB，步长为10G</br>        \- 自动删除</br>            \- 默认自动删除</br>        \- 可以选择已存在的云硬盘</br>        \- 单个容器最多可以挂载 7 个 data volume</br>\- 计费</br>  \- 弹性IP的计费模式，如果选择按用量类型可以单独设置，其它计费模式都以主机为准</br>  \- 云硬盘的计费模式以主机为准</br>\- 容器日志</br>    \- 默认在本地分配10MB的存储空间，自动 rotate</br>\- 其他</br>    \- 创建完成后，容器状态为running</br>    \- maxCount 为最大努力，不保证一定能达到 maxCount</br>|
|**createSecret**|POST|创建一个 secret，用于存放镜像仓库机密相关信息。</br>|
|**deleteContainer**|DELETE|容器状态必须为 stopped、running 或 error状态。 <br></br>按量付费的实例，如不主动删除将一直运行，不再使用的实例，可通过本接口主动停用。<br></br>只能支持主动删除按量计费类型的实例。包年包月过期的容器也可以删除，其它的情况还请发工单系统。计费状态异常的容器无法删除。</br>|
|**deleteSecret**|DELETE|删除单个 secret</br>|
|**describeContainer**|GET|查询一台原生容器的详细信息</br>|
|**describeContainers**|GET|批量查询原生容器的详细信息<br></br>此接口支持分页查询，默认每页20条。</br>|
|**describeQuota**|GET|查询资源的配额，支持：原生容器 和 secret.</br>|
|**describeSecret**|GET|查询单个 secret 详情</br>|
|**describeSecrets**|GET|查询 secret 列表。<br> </br>此接口支持分页查询，默认每页20条。</br>|
|**disassociateElasticIp**|POST|容器解绑公网 IP，解绑的是主网卡、主内网 IP 对应的弹性 IP.</br>|
|**getLogs**|GET|查询单个容器日志</br>|
|**modifyContainerAttribute**|PATCH|修改容器的 名称 和 描述。</br>|
|**startContainer**|POST|启动处于关闭状态的单个容器，处在任务执行中的容器无法启动。<br></br>容器实例或其绑定的云盘已欠费时，容器将无法正常启动。<br></br>|
|**stopContainer**|POST|停止处于运行状态的单个实例，处于任务执行中的容器无法启动。</br>|
