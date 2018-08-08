# 云主机


## 简介
云主机实例、镜像、规格类型、实例模板、配额相关的接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**associateElasticIp**|POST|云主机绑定弹性公网IP，绑定的是主网卡、内网主IP对应的弹性公网IP。&lt;br&gt;
一台云主机只能绑定一个弹性公网IP(主网卡)，若主网卡已存在弹性公网IP，会返回错误。&lt;br&gt;
如果是黑名单中的用户，会返回错误。
|
|**attachDisk**|POST|为一台云主机挂载一块数据盘(云硬盘)，云主机和云硬盘没有正在进行中的的任务时才可挂载。&lt;br&gt;
云主机状态必须是&lt;b&gt;running&lt;/b&gt;或&lt;b&gt;stopped&lt;/b&gt;状态。&lt;br&gt;
本地盘(local类型)做系统盘的云主机可挂载8块数据盘，云硬盘(cloud类型)做系统盘的云主机可挂载7块数据盘。
|
|**attachNetworkInterface**|POST|云主机挂载一块弹性网卡。&lt;br&gt;
云主机状态必须为&lt;b&gt;running&lt;/b&gt;或&lt;b&gt;stopped&lt;/b&gt;状态，并且没有正在进行中的任务才可操作。&lt;br&gt;
弹性网卡上如果绑定了公网IP，那么公网IP所在az需要与云主机的az保持一致，或者公网IP属于全可用区，才可挂载。&lt;br&gt;
云主机挂载弹性网卡的数量，不能超过实例规格的限制。可查询&lt;a href=&quot;https://www.jdcloud.com/help/detail/2901/isCatalog/1&quot;&gt;DescribeInstanceTypes&lt;/a&gt;接口获得指定地域或可用区的规格信息。&lt;br&gt;
弹性网卡与云主机必须在相同vpc下。
|
|**copyImages**|POST|镜像跨区复制，将私有镜像复制到其它地域下，只允许操作您的个人私有镜像。&lt;br&gt;
只支持cloudDisk云盘系统盘类型的镜像。
|
|**createImage**|POST|为云主机创建私有镜像。云主机状态必须为&lt;b&gt;stopped&lt;/b&gt;。&lt;br&gt;
云主机没有正在进行中的任务才可制作镜像。&lt;br&gt;
如果云主机中挂载了数据盘，默认会将数据盘创建快照，生成打包镜像。&lt;br&gt;
调用接口后，需要等待镜像状态变为&lt;b&gt;ready&lt;/b&gt;后，才能正常使用镜像。
|
|**createInstances**|POST|创建一台或多台指定配置的云主机&lt;a href=&quot;https://www.jdcloud.com/help/detail/3383/isCatalog/1&quot;&gt;参数详细说明&lt;/a&gt;&lt;br&gt;
- 创建云主机需要通过实名认证
- 规格类型
    - 可查询&lt;a href=&quot;https://www.jdcloud.com/help/detail/2901/isCatalog/1&quot;&gt;DescribeInstanceTypes&lt;/a&gt;接口获得指定地域或可用区的规格信息。
    - 不能使用已下线、或已售馨的规格ID
- 镜像
    - Windows Server 2012 R2标准版 64位 中文版 SQL Server 2014 标准版 SP2内存需大于1GB；
    - Windows Server所有镜像CPU不可选超过64核CPU。
    - 可查询&lt;a href=&quot;https://www.jdcloud.com/help/detail/2874/isCatalog/1&quot;&gt;DescribeImages&lt;/a&gt;接口获得指定地域的镜像信息。
    - 选择的镜像必须支持选择的规格类型。可查询&lt;a href=&quot;https://www.jdcloud.com/help/detail/2872/isCatalog/1&quot;&gt;DescribeImageConstraints&lt;/a&gt;接口获得指定镜像的规格类型限制信息。&lt;br&gt;
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
    - &lt;a href=&quot;https://www.jdcloud.com/help/detail/3870/isCatalog/1&quot;&gt;参考公共参数规范&lt;/a&gt;
|
|**deleteImage**|DELETE|删除一个私有镜像，只允许操作您的个人私有镜像。
|
|**deleteInstance**|DELETE|删除按配置计费、或包年包月已到期的单个云主机。不能删除没有计费信息的云主机。&lt;br&gt;
云主机状态必须为运行&lt;b&gt;running&lt;/b&gt;、停止&lt;b&gt;stopped&lt;/b&gt;、错误&lt;b&gt;error&lt;/b&gt;，同时云主机没有正在进行中的任务才可删除。&lt;br&gt;
包年包月未到期的云主机不能删除。白名单用户不能删除包年包月已到期的云主机。&lt;br&gt;
如果主机中挂载的数据盘为按配置计费的云硬盘，并且不是共享型云硬盘，并且AutoDelete属性为true，那么数据盘会随主机一起删除。
&lt;/br&gt;敏感操作，可开启&lt;a href=&quot;https://www.jdcloud.com/help/detail/3786/isCatalog/1&quot;&gt;MFA操作保护&lt;/a&gt;|
|**describeImage**|GET|查询镜像详情。
|
|**describeImageConstraints**|GET|查询镜像的规格类型限制。&lt;br&gt;
通过此接口可以查看镜像不支持的规格类型。只有官方镜像、第三方镜像有规格类型的限制，个人的私有镜像没有此限制。
|
|**describeImageConstraintsBatch**|GET|批量查询镜像的规格类型限制。&lt;br&gt;
通过此接口可以查看镜像不支持的规格类型。只有官方镜像、第三方镜像有规格类型的限制，个人的私有镜像没有此限制。
|
|**describeImageMembers**|GET|查询镜像共享帐户列表，只允许操作您的个人私有镜像。
|
|**describeImages**|GET|查询镜像信息列表。&lt;br&gt;
通过此接口可以查询到京东云官方镜像、第三方镜像、私有镜像、或其他用户共享给您的镜像。&lt;br&gt;
此接口支持分页查询，默认每页20条。
|
|**describeInstance**|GET|查询一台云主机的详细信息
|
|**describeInstanceStatus**|GET|批量查询云主机状态|
|**describeInstanceTypes**|GET|查询规格类型信息列表
|
|**describeInstanceVncUrl**|GET|获取云主机vnc，用于连接管理云主机。&lt;br&gt;
vnc地址的有效期为1个小时，调用接口获取vnc地址后如果1个小时内没有使用，vnc地址自动失效，再次使用需要重新获取。
|
|**describeInstances**|GET|批量查询云主机的详细信息&lt;br&gt;
此接口支持分页查询，默认每页20条。
|
|**describeQuotas**|GET|查询配额，支持：云主机、镜像、密钥、模板
|
|**detachDisk**|POST|云主机缷载数据盘，云主机和云硬盘没有正在进行中的任务时才可缷载。&lt;br&gt;
|
|**detachNetworkInterface**|POST|云主机缷载一块弹性网卡。&lt;br&gt;
云主机状态必须为&lt;b&gt;running&lt;/b&gt;或&lt;b&gt;stopped&lt;/b&gt;状态，并且没有正在进行中的任务才可操作。&lt;br&gt;
不能缷载主网卡。
|
|**disassociateElasticIp**|POST|云主机解绑弹性公网IP，解绑的是主网卡、内网主IP对应的弹性公网IP。
|
|**modifyImageAttribute**|POST|修改镜像信息，包括名称、描述；只允许操作您的个人私有镜像。
|
|**modifyInstanceAttribute**|POST|修改云主机部分信息，包括名称、描述。
|
|**modifyInstanceDiskAttribute**|POST|修改云主机挂载的数据盘属性，包括是否随主机删除。
|
|**modifyInstanceNetworkAttribute**|POST|修改虚机弹性网卡属性，包括是否随云主机一起删除。&lt;br&gt;
不能修改主网卡。
|
|**modifyInstancePassword**|POST|修改云主机密码，主机没有正在进行中的任务时才可操作。&lt;br&gt;
修改密码后，需要重启云主机后生效。
|
|**rebootInstance**|POST|重启单个云主机，只能重启&lt;b&gt;running&lt;/b&gt;状态的云主机，云主机没有正在进行中的任务才可重启。
|
|**rebuildInstance**|POST|云主机使用指定镜像重置云主机镜像&lt;br&gt;
云主机的状态必须为&lt;b&gt;stopped&lt;/b&gt;状态。&lt;br&gt;
若当前云主机的系统盘类型为local类型，那么更换的镜像必须为localDisk类型的镜像；同理若当前云主机的系统盘为cloud类型，那么更换的镜像必须为cloudDisk类型的镜像。可查询&lt;a href=&quot;https://www.jdcloud.com/help/detail/2874/isCatalog/1&quot;&gt;DescribeImages&lt;/a&gt;接口获得指定地域的镜像信息。&lt;br&gt;
若不指定镜像ID，默认使用当前主机的原镜像重置系统。&lt;br&gt;
指定的镜像必须能够支持当前主机的规格类型(instanceType)，否则会返回错误。可查询&lt;a href=&quot;https://www.jdcloud.com/help/detail/2872/isCatalog/1&quot;&gt;DescribeImageConstraints&lt;/a&gt;接口获得指定镜像的规格类型限制信息。
|
|**resizeInstance**|POST|云主机变更规格类型&lt;br&gt;
云主机的状态必须为&lt;b&gt;stopped&lt;/b&gt;状态。&lt;br&gt;
16年创建的云硬盘做系统盘的主机，一代与二代规格类型不允许相互调整。&lt;br&gt;
本地盘(local类型)做系统盘的主机，一代与二代规格类型不允许相互调整。&lt;br&gt;
使用高可用组(Ag)创建的主机，一代与二代规格类型不允许相互调整。&lt;br&gt;
云硬盘(cloud类型)做系统盘的主机，一代与二代规格类型允许相互调整。&lt;br&gt;
如果当前主机中的弹性网卡数量，大于规格类型允许的弹性网卡数量，会返回错误。可查询&lt;a href=&quot;https://www.jdcloud.com/help/detail/2901/isCatalog/1&quot;&gt;DescribeInstanceTypes&lt;/a&gt;接口获得指定地域或可用区的规格信息。&lt;br&gt;
当前主机所使用的镜像，需要支持要变更的目标规格类型，否则返回错误。可查询&lt;a href=&quot;https://www.jdcloud.com/help/detail/2872/isCatalog/1&quot;&gt;DescribeImageConstraints&lt;/a&gt;接口获得指定镜像的规格类型限制信息。&lt;br&gt;
云主机欠费时，无法更改规格类型。
|
|**shareImage**|POST|共享镜像，只允许操作您的个人私有镜像，单个镜像最多可共享给20个京东云帐户。&lt;br&gt;
打包镜像目前不支持共享。
|
|**startInstance**|POST|启动单个云主机，只能启动&lt;b&gt;stopped&lt;/b&gt;状态的云主机，云主机没有正在进行中的任务才可启动。&lt;br&gt;
只能启动正常计费状态的云主机。
|
|**stopInstance**|POST|停止单个云主机，只能停止&lt;b&gt;running&lt;/b&gt;状态的云主机，云主机没有正在进行中的任务才可停止
|
|**unShareImage**|POST|取消共享镜像，只允许操作您的个人私有镜像。
|
