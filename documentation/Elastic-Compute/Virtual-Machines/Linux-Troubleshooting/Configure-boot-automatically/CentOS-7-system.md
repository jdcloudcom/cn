# CentOS 7系统

**编写systemd下服务脚本**

Red Hat Enterprise Linux 7（RHEL 7）已经将服务管理工具从SysVinit和Upstart迁移到了systemd上，相应的服务脚本也需要改变。前面的版本里，所有的启动脚本都是放在/etc/rc.d/init.d/ 目录下。这些脚本都是bash脚本，可以让系统管理员控制这些服务的状态，通常，这些脚本中包含了start，stop，restart这些方法，以提供系统自动调用这些方法。但是在RHEL 7中当中已经完全摒弃了这种方法，而采用了一种叫unit的配置文件来管理服务

**Systemd下的unit文件**

Unit文件专门用于systemd下控制资源，这些资源包括服务(service)、套接字(socket)、设备(device)、挂载点(mount point)、自动挂载点(automount point)、交换文件或分区(a swap file or partition)…

所有的unit文件都应该配置[Unit]或者[Install]段.由于通用的信息在[Unit]和[Install]中描述，每一个unit应该有一个指定类型段，例如[Service]来对应后台服务类型unit.

unit 类型如下：

**service**

**socket** ：此类 unit 封装系统和互联网中的一个socket。当下，systemd支持流式, 数据报和连续包的AF\_INET,AF\_INET6,AF\_UNIXsocket 。也支持传统的 FIFOs 传输模式。每一个 socket unit 都有一个相应的服务 unit 。相应的服务在第一个“连接”进入 socket 或 FIFO 时就会启动(例如：nscd.socket 在有新连接后便启动 nscd.service)。

**device** ：此类 unit 封装一个存在于 Linux设备树中的设备。每一个使用 udev 规则标记的设备都将会在 systemd 中作为一个设备 unit 出现。udev 的属性设置可以作为配置设备 unit 依赖关系的配置源。

**mount** ：此类 unit 封装系统结构层次中的一个挂载点。

**automount** ：此类 unit 封装系统结构层次中的一个自挂载点。每一个自挂载 unit 对应一个已挂载的挂载 unit (需要在自挂载目录可以存取的情况下尽早挂载)。

**target** ：此类 unit 为其他 unit 进行逻辑分组。它们本身实际上并不做什么，只是引用其他 unit 而已。这样便可以对 unit 做一个统一的控制。(例如：multi-user.target 相当于在传统使用 SysV 的系统中运行级别5)；bluetooth.target 只有在蓝牙适配器可用的情况下才调用与蓝牙相关的服务，如：bluetooth 守护进程、obex 守护进程等）

**snapshot** ：与 targetunit 相似，快照本身不做什么，唯一的目的就是引用其他 unit 。

**认识service的unit文件**

扩展名：.service

路径：

*/etc/systemd/system/**     ――――  供系统管理员和用户使用

*/run/systemd/system/**     ――――  运行时配置文件

*/usr/lib/systemd/system/**   ――――  安装程序使用（如RPM包安装）



以下是一段service unit文件的例子，属于/usr/lib/systemd/system/NetworkManager.service文件，它描述的是系统中的网络管理服务。



*[Unit]*

*Description=Network Manager*

*Wants=network.target*

*Before=network.target network.service*

*[Service]*

*Type=dbus*

*BusName=org.freedesktop.NetworkManager*

*ExecStart=/usr/sbin/NetworkManager --no-daemon*

*# NM doesn't want systemd to kill its children for it*

*KillMode=process*

*[Install]*

*WantedBy=multi-user.target*

*Alias=dbus-org.freedesktop.NetworkManager.service*

*Also=NetworkManager-dispatcher.service*



整个文件分三个部分，**[Unit]·[Service]·[Install]**

**[Unit]**：记录unit文件的通用信息。

**[Service]**：记录Service的信息

**[Install]**：安装信息。



**Unit主要包含以下内容：**

●  **Description**：对本service的描述。

●  **Before, After**：定义启动顺序，Before=xxx.service，代表本服务在xxx.service启动之前启动。After=xxx.service,代表本服务在xxx之后启动。

●  **Requires**: 这个单元启动了，那么它“需要”的单元也会被启动; 它“需要”的单元被停止了，它自己也活不了。但是请注意，这个设定并不能控制某单元与它“需要”的单元的启动顺序（启动顺序是另外控制的），即 Systemd 不是先启动 Requires 再启动本单元，而是在本单元被激活时，并行启动两者。于是会产生争分夺秒的问题，如果 Requires 先启动成功，那么皆大欢喜; 如果 Requires 启动得慢，那本单元就会失败（Systemd 没有自动重试）。所以为了系统的健壮性，不建议使用这个标记，而建议使用 Wants 标记。可以使用多个 Requires。

●  **RequiresOverridable**：跟 Requires 很像。但是如果这条服务是由用户手动启动的，那么 RequiresOverridable 后面的服务即使启动不成功也不报错。跟 Requires 比增加了一定容错性，但是你要确定你的服务是有等待功能的。另外，如果不由用户手动启动而是随系统开机启动，那么依然会有 Requires 面临的问题。

●  **Requisite**：强势版本的 Requires。要是这里需要的服务启动不成功，那本单元文件不管能不能检测等不能等待都立刻就会失败。

●  **Wants**：推荐使用。本单元启动了，它“想要”的单元也会被启动。但是启动不成功，对本单元没有影响。

●  **Conflicts**：一个单元的启动会停止与它“冲突”的单元，反之亦然。



**Service主要包含以下内容：**

●  **Type：service**的种类，包含下列几种类型：

----simple 默认，这是最简单的服务类型。意思就是说启动的程序就是主体程序，这个程序要是退出那么一切都退出。

-----forking 标准 Unix Daemon 使用的启动方式。启动程序后会调用 fork() 函数，把必要的通信频道都设置好之后父进程退出，留下守护精灵的子进程

-----oneshot种服务类型就是启动，完成，没进程了。

notify,idle类型比较少见，不介绍。

●  **ExecStart**：服务启动时执行的命令，通常此命令就是服务的主体。

------如果你服务的类型不是 oneshot，那么它只可以接受一个命令，参数不限。

------多个命令用分号隔开，多行用 \ 跨行。

●  **ExecStartPre, ExecStartPost：ExecStart**执行前后所调用的命令。

●  **ExecStop**：定义停止服务时所执行的命令，定义服务退出前所做的处理。如果没有指定，使用systemctl stop xxx命令时，服务将立即被终结而不做处理。

●  **Restart**：定义服务何种情况下重启（启动失败，启动超时，进程被终结）。可选选项：no, on-success, on-failure,on-watchdog, on-abort

●  **SuccessExitStatus**：参考ExecStart中返回值，定义何种情况算是启动成功。

eg：SuccessExitStatus=1 2 8 SIGKILL

**Install主要包含以下内容：**

●  **WantedBy**：何种情况下，服务被启用。

eg：WantedBy=multi-user.target（多用户环境下启用）

●  **Alias**：别名



旧的命令与systemd命令的映射
service systemctl Description
service name start ----> systemctl start name.service ●Starts a service.
service name stop ----> systemctl stopname.service ●Stops a service.
service name restart ----> systemctl restartname.service ●Restarts a service.
service name condrestart ---->
systemctl try-restart name.service ●Restarts a service only if it is running.
service name reload ----> systemctl reloadname.serviceReloads configuration.
service name status ----> systemctl status name.service
systemctl is-active name.service
●Checks if a service isrunning.
service --status-all ----> systemctl list-units –type service --all
●Displays the status of all services.chkconfig systemctl
chkconfig name on ----> systemctl enablename.service ●Enables a service.
chkconfig name off ----> systemctl disablename.service ●Disables a service.
chkconfig --list name ----> systemctl statusname.service
system ctl is-enabled name.service
●Checks if a service is enabled.
chkconfig --list ----> systemctl list-unit-files –type service
●Lists all services and checks if they are enabled.



**创建自己的systemd服务**

弄清了unit文件的各项意义，我们可以尝试编写自己的服务，与以前用SysV来编写服务相比，整个过程比较简单。unit文件有着简洁的特点，是以前臃肿的脚本所不能比的。

在本例中，尝试写一个命名为my-demo.service的服务，整个服务很简单：在开机的时候将服务启动时的时间写到一个文件当中。可以通过这个小小的例子来说明整个服务的创建过程。

**Step1**：编写属于自己的unit文件，命令为my-demo.service，整个文件如下：

[Unit]
Description=My-demo Service

[Service]
Type=oneshot
ExecStart=/bin/bash /root/test.sh
StandardOutput=syslog
StandardError=inherit

[Install]
WantedBy=multi-user.target



**Step2**：将上述的文件拷贝到RHEL 7系统中/usr/lib/systemd/system/*目录下

**Step3**：编写unit文件中ExecStart=/bin/bash /root/test.sh所定义的test.sh文件，将其放在定义的目录当中，此文件是服务的执行主体。文件内容如下：

*#!/bin/bash*

*date >> /tmp/date*

Step4：将my-demo.service注册到系统当中并设置开机自启动执行命令：

*# systemctl enable my-demo.service*

输出：ln -s'/usr/lib/systemd/system/my-demo.service' '/etc/systemd/system/multi-user.target.wants/my-demo.service'

输出表明，注册的过程实际上就是将服务链接到/etc/systemd/system/目录下。

至此服务已经创建完成。重新启动系统，会发现/tmp/date文件已经生成，服务在开机时启动成功。当然本例当中的test.sh文件可以换成任意的可执行文件作为服务的主体，这样就可以实现各种各样的功能。



**对于已经安装的服务的设置开机自启动**

这里举个设置SSHD开机自启动的例子：

#查看SSHD服务是否启动

*systemctl status sshd*

请注意，如果已经有enabled标记，表示该服务会开机自启动。如果是disabled 则表示不会开机自启动，需要执行如下指令设置开机自启动：

*systemctl enable sshd*
