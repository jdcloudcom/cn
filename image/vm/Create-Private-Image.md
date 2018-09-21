# 制作私有镜像
您可以根据自己的需要，通过已经创建的云主机创建私有镜像，并使用这个镜像启动更多与原主机具有相同操作系统、预装的软件以及相关配置的实例。
### 制作私有镜像限制
用户可以通过官方镜像创建实例，并自行安装及配置软件环境。之后可以基于此实例创建私有镜像，由于实例运行中创建私有镜像，会导致正在读写的数据无法保存，京东云仅支持主机“停止”状态下制作私有镜像。

对于Linux系统，若该实例在/etc/fstab内配置了自动挂载命令，制作私有镜像前还请删除相关自动挂载命令，否则基于其私有镜像创建的实例可能无法正常启动。
### 通过控制台，从实例创建私有镜像
1. 访问[云主机控制台][1]，即进入实例列表页面。或访问[京东云控制台][2]点击左侧导航栏【弹性计算】-【云主机】-【实例】进入实例列表页。
2. 选定要创建镜像的实例，点击“更多”操作中的【制作镜像】。
![](../../../../../image/vm/Operation-Guide-Image-create1.png)

3. 在“创建镜像”的弹窗中，完成对私有镜像“名称”、“描述”的补充，点击【确定】，开始私有镜像创建。
4. 除对系统盘制作镜像以外，您可以选择实例当前挂载的数据盘一同制作快照，此过程制作的快照会与系统盘镜像进行关联，并显示在私有镜像详情页中的“设备映射信息”中,作为后续使用该私有镜像创建实例时数据盘的预设配置，方便快速整机部署。如果您希望对数据盘的容量进行修改可在基于该镜像创建主机时调整。点此详见数据盘[设备名分配规则](../Operation-Guide/Cloud-Disk/Assign-Device-Name.md)。
5. 制作整机镜像耗时较长，为避免制作失败，请在制作过程中停止对主机和云硬盘的其他操作，同时请确保您当前实例和云硬盘快照的配额充足。
![](../../../../../image/vm/Operation-Guide-Image-create2.png)
![](../../../../../image/vm/Operation-Guide-Image-create3.png)

6. 提交的私有镜像，经过“创建中”，“复制中”两个中间状态，最终创建完成，变为“可用”状态，可以正常使用。中间状态，不可对镜像进行【共享】，【创建云主机】，【删除】操作。

7. 制作镜像过程中，任一资源创建失败均会导致镜像为“错误”状态，如选择了主机挂载的数据盘制作整机镜像，则操作失败会自动删除此次操作创建的所有快照，私有镜像需要您自行确认后删除。
![](../../../../../image/vm/Operation-Guide-Image-create4.png)
 
 ## 相关参考
 
[设备名分配规则](../Operation-Guide/Cloud-Disk/Assign-Device-Name.md)


  [1]: https://cns-console
  [2]: https://console.jdcloud.com/
  [3]: ./images/Operation-Guide-Image-create1.png "Operation-Guide-Image-create1.png"
  [4]: ./images/Operation-Guide-Image-create2.png "Operation-Guide-Image-create2.png"
  [5]: ./images/Operation-Guide-Image-create3.png "Operation-Guide-Image-create3.png"
  [6]: ./images/Operation-Guide-Image-create4.png "Operation-Guide-Image-create4.png"