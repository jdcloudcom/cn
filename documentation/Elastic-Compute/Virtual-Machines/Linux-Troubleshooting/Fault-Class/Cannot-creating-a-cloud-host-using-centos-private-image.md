# 使用centos私有镜像创建云主机后无法获取内网IP解决办法



有时使用之前制作的centos私有镜像创建云主机后发现云主机未获取内网IP，ifconfig -a查看网络信息发现网卡名称变为eth1，且没有内网IP信息，如图所示：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/%E4%BD%BF%E7%94%A8centos%E7%A7%81%E6%9C%89%E9%95%9C%E5%83%8F%E5%88%9B%E5%BB%BA%E4%BA%91%E4%B8%BB%E6%9C%BA%E5%90%8E%E6%97%A0%E6%B3%95%E8%8E%B7%E5%8F%96%E5%86%85%E7%BD%91IP%E8%A7%A3%E5%86%B3%E5%8A%9E%E6%B3%9501.png)

这是由于创建私有镜像时保留了网卡的UUID信息，导致使用私有镜像创建云主机时，系统自动分配网卡为eth1，而/etc/sysconfig/network-scripts下又没有ifcfg-eth1配置文件（只有原有的ifcfg-eth0文件），导致系统有eth0的配置文件但找不到eth0设备，有eth1设备但没有eth0配置文件，所以无法获取内网IP，同时公网IP也无法访问。

解决办法：

执行
*vi /etc/udev/rules.d/70-persistent-net.rules*

如图所示：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/%E4%BD%BF%E7%94%A8centos%E7%A7%81%E6%9C%89%E9%95%9C%E5%83%8F%E5%88%9B%E5%BB%BA%E4%BA%91%E4%B8%BB%E6%9C%BA%E5%90%8E%E6%97%A0%E6%B3%95%E8%8E%B7%E5%8F%96%E5%86%85%E7%BD%91IP%E8%A7%A3%E5%86%B3%E5%8A%9E%E6%B3%9502.png)

可以看到系统在原有eth0网卡的内容（红框）下自动生成了eth1的内容（黄框）。

修改文件，将eth0部分的内容注释掉，将eth1内容中的设备名改为eth0，如下图两处红框所示，wq保存文件并退出。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/%E4%BD%BF%E7%94%A8centos%E7%A7%81%E6%9C%89%E9%95%9C%E5%83%8F%E5%88%9B%E5%BB%BA%E4%BA%91%E4%B8%BB%E6%9C%BA%E5%90%8E%E6%97%A0%E6%B3%95%E8%8E%B7%E5%8F%96%E5%86%85%E7%BD%91IP%E8%A7%A3%E5%86%B3%E5%8A%9E%E6%B3%9503.png)

reboot重启云主机，重启后，执行ifconfig -a发现之前的eth1设备名恢复为eth0且可以获取内网IP，绑定公网IP后也可以正常访问，如图：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/%E4%BD%BF%E7%94%A8centos%E7%A7%81%E6%9C%89%E9%95%9C%E5%83%8F%E5%88%9B%E5%BB%BA%E4%BA%91%E4%B8%BB%E6%9C%BA%E5%90%8E%E6%97%A0%E6%B3%95%E8%8E%B7%E5%8F%96%E5%86%85%E7%BD%91IP%E8%A7%A3%E5%86%B3%E5%8A%9E%E6%B3%9504.png)

如无法解决您的问题，请向我们提工单。
