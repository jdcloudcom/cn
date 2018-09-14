## 一.普通情况创建主机最小化参数

    创建本地盘做系统盘的云主机
    {
        "InstanceSpec":{
            "az":"cn-north-1a",
            "name":"test",
            "imageId":"bba85cab-dfdc-4359-9218-7a2de429dd80",
            "instanceType":"g.n2.medium",
            "systemDisk":{
                "diskCategory":"local"
            },
            "primaryNetworkInterface":{
                "networkInterface":{
                    "subnetId":"subnet-2yl2n4hqte"
                }
            }
        }
    }
    创建云硬盘做系统盘的主机
    {
        "InstanceSpec":{
            "az":"cn-north-1a",
            "name":"test",
            "imageId":"bba85cab-dfdc-4359-9218-7a2de429dd80",
            "instanceType":"g.n2.medium",
            "systemDisk":{
                "diskCategory":"cloud",
                "CloudDiskSpec":{
                    "DiskType":"ssd",
                    "DiskSizeGB":50
                }
            },
            "primaryNetworkInterface":{
                "networkInterface":{
                    "subnetId":"subnet-2yl2n4hqte"
                }
            }
        }
    }
### 必选参数:
|字段名|描述|
|-|-|
|InstanceSpec.Name         | 云主机名称|
|InstanceSpec.Az           | 可用区|
|InstanceSpec.ImageId      | 镜像ID|
|InstanceSpec.InstanceType | 规格类型|
|InstanceSpec.PrimaryNetworkInterface.networkInterface.subnetId | 子网ID|
|InstanceSpec.SystemDisk   | 系统盘配置|
|InstanceSpec.SystemDisk.DiskCategory| 磁盘分类，用于标识是创建本地盘系统盘的云主机，还是云硬盘系统盘的云主机。取值需要与镜像类型匹配，localDisk类型镜像需传"local"，cloudDisk类型镜像需传"cloud"。<br>传入"local"时，系统盘不计费，SystemDisk下的其余参数无效。<br>传入"cloud"时，云硬盘计费方式与云主机保持一致|
|InstanceSpec.SystemDisk.CloudDiskSpec.DiskType| 云硬盘类型，云硬盘做系统盘时必传|
|InstanceSpec.SystemDisk.CloudDiskSpec.DiskSizeGB| 云硬盘大小[40-500GB]，不能小于镜像系统盘的大小，云硬盘做系统盘时必传|

### 可选参数:
|字段名|描述|
|-|-|
|MaxCount|创建数量，默认为1|
|InstanceSpec.Charge|云主机计费方式，若不指定，默认按配置计费，云主机计费方式只支持按配置或包年包月|
|InstanceSpec.Description|云主机描述|
|InstanceSpec.Password|云主机密码|
|InstanceSpec.KeyNames|密钥名称|
|InstanceSpec.SystemDisk.CloudDiskSpec.AutoDelete|系统盘是否随主机删除。如果创建的是本地盘系统盘，此参数强制为true；如果创建的是云硬盘系统盘的主机，默认与镜像中的配置保持一致。<br>按配置计费时可指定为true，包年包月强制默认false|
|InstanceSpec.PrimaryNetworkInterface.NetworkInterface.PrimaryIpAddress|主网卡主内网IP地址，指定此参数后，MaxCount只能为1|
|InstanceSpec.PrimaryNetworkInterface.DeviceIndex|主网卡设备Index只能是1|
|InstanceSpec.PrimaryNetworkInterface.AutoDelete|主网卡随主机删除。主网卡只能是true|
|InstanceSpec.DataDisks| 数据盘，数据盘计费方式强制与云主机计费方式保持一致。|
|InstanceSpec.DataDisks.n.DiskCategory|必选参数(创建数据盘时)磁盘分类，必须为cloud|
|InstanceSpec.DataDisks.n.DeviceName| 可选参数，数据盘逻辑挂载点|
|InstanceSpec.DataDisks.n.AutoDelete| 可选参数，是否随主机删除，按配置计费默认为true，包年包月强制默认为false|
|InstanceSpec.DataDisks.n.NoDevice| 可选参数，可以排除打包镜像中、或者模板中对应DeviceName的设备|
|InstanceSpec.DataDisks.n.CloudDiskSpec.Name| 可选参数，数据盘名称|
|InstanceSpec.DataDisks.n.CloudDiskSpec.Description| 可选参数，数据盘描述|
|InstanceSpec.DataDisks.n.CloudDiskSpec.DiskType|必选参数(创建数据盘时)，数据盘类型|
|InstanceSpec.DataDisks.n.CloudDiskSpec.DiskSizeGB| 必选参数(创建数据盘时)，数据盘大小|
|InstanceSpec.DataDisks.n.CloudDiskSpec.SnapshotId| 可选参数，使用快照创建数据盘|
|InstanceSpec.ElasticIp| 公网IP，默认为按用量计费，如不指定计费参数或者不是按用量计费时，则强制与云主机计费方式保持一致。|
|InstanceSpec.ElasticIp.BandwidthMbps| 必选参数(创建公网IP时)，带宽大小|
|InstanceSpec.ElasticIp.Provider| 可选参数，默认为BGP|
|InstanceSpec.ElasticIp.ChargeSpec| 可选参数，默认为按用量计费|
|ClientToken| 支持幂等性的uuid|


## 二.使用AG创建主机最小化参数
    {
        "instanceSpec": {
            "agId":"ag-nm9ebd1z8n",
            "name":"test"
        }
    }
### 必选参数:
|字段名|描述|
|-|-|
|InstanceSpec.Name| 云主机名称|
|InstanceSpec.AgId| 高可用组ID|
### 可选参数:
|字段名|描述|
|-|-|
|MaxCount| 创建数量，默认为1|
|InstanceSpec.Charge| 云主机计费方式，若不指定，默认按配置计费，云主机计费方式只支持按配置或包年包月|
|InstanceSpec.Description|云主机描述|
|InstanceSpec.PrimaryNetworkInterface.NetworkInterface.PrimaryIpAddress| 主网卡主内网IP地址，指定此参数后，MaxCount只能为1|
|ClientToken| 支持幂等性的uuid|

## 三.使用模板创建主机最小化参数
    {
        "instanceSpec": {
            "instanceTemplateId":"it-a7j208hj93",
            "name":"xx",
            "az":"cn-north-1a"
        }
    }
### 必选参数:
|字段名|描述|
|-|-|
|InstanceSpec.Name| 云主机名称|
|InstanceSpec.Az| 可用区|
|InstanceSpec.InstanceTemplateId| 启动模板ID|
### 可选参数: 若指定的参数与模板中的参数冲突，会强制覆盖模板中的参数
|字段名|描述|
|-|-|
|InstanceSpec.ImageId| 镜像ID，若指定了与模板中不一致的镜像ID，那么模板中的数据盘dataDisks参数会失效|
|InstanceSpec.InstanceType| 规格类型|
|InstanceSpec.SystemDisk| 系统盘配置|
|InstanceSpec.SystemDisk.DiskCategory| 磁盘分类，用于标识是创建本地盘系统盘的云主机，还是云硬盘系统盘的云主机。取值需要与镜像类型匹配，localDisk类型镜像需传"local"，cloudDisk类型镜像需传"cloud"。<br>传入"local"时，系统盘不计费，SystemDisk下的其余参数无效。<br>传入"cloud"时，云硬盘计费方式与云主机保持一致|
|InstanceSpec.SystemDisk.CloudDiskSpec.DiskType| 云硬盘类型|
|InstanceSpec.SystemDisk.CloudDiskSpec.DiskSizeGB| 云硬盘大小，不能小于镜像系统盘的大小|
|InstanceSpec.SystemDisk.CloudDiskSpec.AutoDelete| 是否随主机删除，默认与镜像中的配置保持一致。按配置计费可指定为true，包年包月强制默认false|
|MaxCount| 创建数量，默认为1|
|InstanceSpec.Charge| 云主机计费方式，若不指定，默认按配置计费，云主机计费方式只支持按配置或包年包月|
|InstanceSpec.Description| 云主机描述|
|InstanceSpec.Password| 云主机密码|
|InstanceSpec.KeyNames| 密钥名称|
|InstanceSpec.PrimaryNetworkInterface.networkInterface.subnetId| 子网ID|
|InstanceSpec.PrimaryNetworkInterface.NetworkInterface.PrimaryIpAddress| 主网卡主内网IP地址，指定此参数后，MaxCount只能为1|
|InstanceSpec.PrimaryNetworkInterface.DeviceIndex| 主网卡设备Index只能是1|
|InstanceSpec.PrimaryNetworkInterface.AutoDelete| 主网卡随主机删除，只能是true|
|InstanceSpec.DataDisks| 数据盘，数据盘计费方式强制与云主机计费方式保持一致。|
|InstanceSpec.DataDisks.n.DiskCategory| 必选参数(创建数据盘时)，必须为cloud|
|InstanceSpec.DataDisks.n.DeviceName| 可选参数|
|InstanceSpec.DataDisks.n.AutoDelete| 可选参数，是否随主机删除，按配置计费默认true，包年包月强制默认alse|
|InstanceSpec.DataDisks.n.NoDevice| 可选参数，可以排除打包镜像中、或者模板中对应DeviceName的设备|
|InstanceSpec.DataDisks.n.CloudDiskSpec.Name| 可选参数，数据盘名称|
|InstanceSpec.DataDisks.n.CloudDiskSpec.Description| 可选参数，数据盘描述|
|InstanceSpec.DataDisks.n.CloudDiskSpec.DiskType| 必选参数(创建数据盘时)，数据盘类型|
|InstanceSpec.DataDisks.n.CloudDiskSpec.DiskSizeGB| 必选参数(创建数据盘时)，数据盘大小|
|InstanceSpec.DataDisks.n.CloudDiskSpec.SnapshotId| 可选参数，使用快照创建数据盘|
|InstanceSpec.ElasticIp| 公网IP，默认为按用量计费，如不指定计费参数或者不是按用量计费时，则强制与云主机计费方式保持一致。|
|InstanceSpec.ElasticIp.BandwidthMbps| 必选参数，带宽大小|
|InstanceSpec.ElasticIp.Provider| 可选参数，默认为BGP|
|InstanceSpec.ElasticIp.ChargeSpec| 可选参数，默认为按用量计费|
|ClientToken| 支持幂等性的uuid|
