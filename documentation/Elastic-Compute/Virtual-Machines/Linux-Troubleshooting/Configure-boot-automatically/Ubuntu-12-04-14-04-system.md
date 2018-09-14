# Ubuntu 12.04-14.04系统

**方法1：ln -s 建立启动软连接**

通过# runlevel查看当前系统的运行级别

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%2012.04-14.04%E7%B3%BB%E7%BB%9F01.png)

上图中 “N 2”中2表示运行级别为2，在ubuntu系统下2~5都是完整的多用户模式。默认情况下。

在ubuntu中有7种运行级别，每种运行级别分别对应着/etc/ rc[0~6].d这7个目录

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%2012.04-14.04%E7%B3%BB%E7%BB%9F02.png)

这7个目录中，每个目录分别存放着对应运行级别加载时需要关闭或启动的服务。由详细信息可知，每个脚本文件都对应着/etc/init.d/目录下具体的服务。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%2012.04-14.04%E7%B3%BB%E7%BB%9F03.png)

K开头的脚本文件代表运行级别加载时需要关闭的，S开头的代表需要执行。因此，当我们需要开机启动自己的脚本时，只需要将可执行脚本丢在/etc/init.d目录下，然后在/etc/rc*.d中建立软链接即可：

*[root@localhost ~]# ln -s /etc/init.d/sshd /etc/rc2.d/S100ssh*

此处sshd是具体服务的脚本文件，S100ssh是其软链接，S开头代表加载时自启动。如果需要在多个运行级别下设置自启动，则需建立多个软链接。这种方式比较繁琐，适用于自定义的服务脚本

**方法2：在/etc/rc.local中添加服务启动命令行**

Ubuntu开机之后会执行/etc/rc.local文件中的脚本，所以直接在/etc/rc.local中添加启动脚本即可实现服务自启动。要注意的是要添加的语句需在exit 0 前面。
