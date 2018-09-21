# SSH登录报fatal: mm_request_send: write: Broken pipe




注意：本文相关 Linux 配置及说明已在 CentOS 6.5 64 位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。



**问题描述：**

客户端连接 Linux 云主机时，命令行或 secure 日志出现类似如下错误信息：

*• fatal: mm_request_send: write: Broken pipe.*

*• Connection closed by 192.168.0.1.*




**问题原因：**

该问题可能是由于 udev-fall 等病毒影响了 SSH 服务的正常运行所致。



**解决办法：**

临时恢复：

以 udev-fall 病毒为例，可尝试通过如下方式，临时恢复 SSH 服务的正常运行：

1.通过 vnc 进入系统。

2.使用如下指令查询病毒进程：


*ps aux | grep udev-fall*

*root     24486  0.0  0.0 108340  1848 pts/0    S    10:30   0:00 /usr/bin/udev-fall*

说明：其中第二列的数字表示进程 ID（PID）。



3.使用如下指令结束病毒进程：


*kill -9 <进程对应 PID>*

比如：

*kill -9 24486*

4.使用如下指令取消病毒服务的自动运行：


*chkconfig udev-fall off*

5.使用如下指令删除病毒程序相关指令和自启动配置：


*rm -rf /usr/bin/udev-fall*

*rm -rf /etc/init.d/udev-fall*

6.使用如下指令重启 SSH 服务，然后从客户端尝试重新连接：


*service sshd restart*


可靠的处理办法：

由于无法明确病毒或者恶意入侵者，是否对系统做过其它篡改，或隐藏了其它病毒文件。所以，为了服务器的长期稳定运行，建议通过系统盘重置的方式，来将服务器恢复到正常状态。



如无法解决您的问题，请向我们提工单。
