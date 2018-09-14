
# 部署StorageClass

StorageClass为Kubernetes集群提供了描述存储类别（class）的方法，包含provisioner、parameters 和 reclaimPolicy等字段，当 class 需要动态分配持久化存储时会使用到。

京东云为Kubernetes集群提供了自定义卷插件kubernetes.io/jdcloud-ebs，将provisioner定义为京东云自定义卷插件，可以使用京东云云硬盘为Kubernetes集群提供持久化存储。目前，在Kubernetes集群服务中，提供三种storageclass，详情参考下图:





您也可以创建自定义的Storageclass：

kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mystorageclass-hdd1
provisioner: kubernetes.io/jdcloud-ebs
parameters:
  zones: cn-north-1a, cn-north-1b
  fstype: ext4
reclaimPolicy: Retain
参数说明：

provisioner：设置参数值为kubernetes.io/jdcloud-ebs，且不可修改，标识使用京东云云硬盘Provisioner插件创建。例如:

type：设置参数值为ssd或premium-hdd，分别对应京东云的SSD云盘和高效云盘；

fstype：设置文件系统类型，可选参数值为fstype和ext4，如未指定fstype，将使用ext4作为默认的文件系统类型；例如：fstype=ext4；

zone：设置云硬盘所在的可用区；

在支持单可用区的地域，您可以不设置该参数；

在支持多可用区的地域，您可以选择某一可用区或选择全部可用区（参数值之间使用","分隔），例如：zones=cn-north-1a, cn-north-1b，选择全部可用区时，新建的云硬盘将根据名称hash算法，被随机分配到某一可用区；

地域与可用区的对应关系参考下表：

华北-北京	可用区A	cn-north-1a
华北-北京	可用区B	cn-north-1b
华东-宿迁	可用区A	cn-east-1a
华东-上海	可用区A	cn-east-2a
华东-上海	可用区B	cn-east-2b
华南-广州	可用区A	cn-south-1a
您可在创建持久化存储声明时，使用StorageClassName指定相应的云硬盘类型；

更多StorageClass参数详情，参考Kubernetes 参数说明文档；
说明：

由 storage class 动态创建的 Persistent Volume 会在的 reclaimPolicy 字段中指定回收策略，可以是 Delete 或者 Retain。如果 StorageClass 对象被创建时没有指定 reclaimPolicy ，它将默认为 Delete。
通过 storage class 手动创建并管理的 Persistent Volume 会使用它们被创建时指定的回收政策；

由 storage class 动态创建的 Persistent Volume 将使用 class 中 mountOptions 字段指定的挂载选项。如果卷插件不支持挂载选项，却指定了该选项，则分配操作失败。 安装选项在 class 和 PV 上都不会做验证，所以如果挂载选项无效，那么这个 PV 就会失败；

Storage class 具有描述属于 storage class 卷的参数。取决于分配器，可以接受不同的参数。 例如，京东云参数 type 的值 为ssd和premium-hdd。当参数被省略时，会使用默认值

 