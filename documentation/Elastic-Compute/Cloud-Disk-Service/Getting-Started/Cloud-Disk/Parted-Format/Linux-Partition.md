# Linux分区、格式化和创建文件系统

<br>

##  使用脚本完成数据盘的分区、格式化及挂载
<br>

在Linux系统下您可以使用京东云提供的脚本检测是否有尚未分区的数据盘，自动完成数据盘的格式化并挂载，省去了您输入复杂的命令和步骤。

<p><a title="挂载脚本.zip" href="http://img1.jcloudcs.com/cms/6bbc4a45-02ce-460d-9696-c31f3fa18c6f20170728174252.zip" target="_self"><span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">挂载脚本.zip</span></a>
</p>
<br>
您可以通过如下两种方式使用该脚本：

1.不带任何参数：该脚本会自动将您所有未分区的设备进行分区、格式化、挂载（默认挂载点为jddata1、jddata2……jddatan）操作，并在/etc/fstab文件中通过UUID的方式实现云硬盘自动挂载

</p>
<pre class="brush:as3;toolbar:false;">sh
sh auto_fdisk.sh</pre>
<p>

2.带设备名（如/dev/vdc等）、挂载点、文件系统参数：该脚本会根据您输入参数自动完成分区、格式化、挂载操作。

</p>
<pre class="brush:as3;toolbar:false;">sh
sh auto_fdisk.sh /dev/vdb jddata1 ext4</pre>
<p>

**注意：**

1.由于相关操作可能会导致数据丢失。 所以，执行操作之前，请务必确保已经通过快照等手段对数据进行有效备份，或明确相关数据丢失无影响；

2.本脚本仅适用于未分区且未挂载的云硬盘，对于硬盘已经分区或挂载的硬盘，不会进行操作；

3.本脚本默认为硬盘创建一个分区，且不可修改；

4.本脚本会将磁盘的UUID和挂载信息写入/etc/fstab文件实现云硬盘自动挂载，如您需要卸载云硬盘，请将/etc/fstab对应的信息删除，否则可能造成云主机无法正常启动。
手动完成数据盘的分区、格式化及挂载

## 手动完成数据盘的分区、格式化及挂载

如您需要手动进行分区、格式化并创建文件系统，我们以Centos操作系统为例，说明如下：

1.在控制台完成挂载后，您在云主机中就可以看到一块未经分区、格式化的磁盘，您可以通过如下命令来查看磁盘分区信息：

```
fdisk -l
```

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/parted-format/parted_001.png)

2.您可以通过如下命令完成分区，/dev/vdb请您修改为需要分区的设备名

```
fdisk /dev/vdb

```

输入命令后，依次输入 n, p, 1, 以及 两次回车，然后是 wq，完成保存。 这样再次通过 fdisk -l 查看时，你可以看到新建的分区/dev/vdb1


![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/parted-format/parted_002.png)

注：如您创建的硬盘容量大于2T，请不要使用分区或参考如下步骤使用parted分区：

1）创建分区表，选择GPT格式：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/parted-format/parted_003.png)

2）创建分区

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/parted-format/parted_004.jpg)

3）再次运行fdisk -l命令，确认分区

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/parted-format/parted_005.jpg)

3.之后您需要对分区后的硬盘进行格式化，命令如下

```
mkfs -t ext4 /dev/vdb1
```



![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/parted-format/parted_006.png)


备注：本示例创建了ext4格式的文件系统，您也可以选择创建其他文件系统。为了从文件系统层面保证数据的完整性和可用性，不建议使用ext2等不提供jounral机制的格式。

4.在mnt目录下创建vdb1目录，并将磁盘挂载到该目录下，方便管理


```
mkdir -p /mnt/vdb1 && mount -t ext4 /dev/vdb1 /mnt/vdb1
```

5.查看磁盘的UUID

```
blkid /dev/vdb1
```
6.写入/etc/fstab文件实现云硬盘挂载
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/parted-format/parted_007.png)


**请注意，若系统为Centos 7以上，写入fstab时必须使用nofail参数，否则若对当前云主机制作私有镜像，基于该私有镜像创建的新云主机将无法正常启动。**

