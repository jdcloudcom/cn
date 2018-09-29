# SSH 连接时出现如下错误：error Could not get shadow infromation for root



注意：本文相关 Linux 配置及说明已在 CentOS 6.5 64 位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。



**问题描述：**

当使用 SSH 登录 Linux 云主机时，即便正确输入了密码，在命令行或 secure 日志中也会出现类似如下错误信息，导致连接失败：

*Permission denied, please try again.*

*error: Could not get shadow infromation for root.*



**问题原因：**

该问题通常是由于系统启用了 SELinux 所致。



**处理办法：**

查看 SELinux 状态

1.通过 vnc 进入系统

2.使用如下指令查看当前SELinux运行状态：


*/usr/sbin/sestatus  -v*

执行结果 

*SELinux status:                 enabled*

如果 status 值为 enabled，则说明已经启用了 SELinux。



临时关闭 SELinux 

1.通过 vnc 进入系统

2.使用如下指令临时关闭SELinux：


*setenforce 0*

3.从客户端再次尝试连接服务器。如果能正常登录，则确认是SELinux配置导致的问题。如果还是无法正常登录，则需要继续排查分析。



永久关闭 SELinux

1.通过 vnc 进入系统

2.如果需要修改相关配置，在继续之前建议进行文件备份。

3.使用 vi 等编辑器，编辑 /etc/selinux/config 文件，修改或进行如下设置：


*SELINUX=disabled*

4.重启服务器，用以永久禁用SELinux



如无法解决您的问题，请向我们提工单。
