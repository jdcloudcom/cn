# SSH 连接时出现如下错误：pam_limits(sshd:session)：could not sent limit for 'nofile'



注意：本文相关配置及说明已在 CentOS 6.5 64 位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。



**问题描述：**

客户端连接 Linux 云主机时，命令行或 secure 日志出现类似如下错误信息：

*-bash: fork: retry: Resource temporarily unavailable.*

*pam_limits(sshd:session)：could not sent limit for 'nofile':operaton not permitted.*

*Permission denied.*



**问题原因：**

该问题通常是由于 shell 进程所占用资源，超出服务器 ulimit 限额所致。



**处理办法：**

**CentOS 6 之前版本操作系统**

对于 Cent OS（包含 RHEL）6.0之前版本操作系统，通过 /etc/security/limits.d/90-nproc.conf 进行全局资源控制。要解决该问题，请进行如下配置检查或修改：

1.通过 vnc 进入系统

2.使用 cat 等指令查看 /etc/security/limits.conf，执行：

*cat /etc/security/limits.conf*

中是否包含类似如下设置：


 #End of file* soft nofile 65535* hard nofile 65535

说明：

默认情况下，未启用上述配置。

第一列的 * 号，表示针对所有用户生效。也可以修改为指定的用户名，表示只对指定的用户生效。



3.如果需要修改相关配置，在继续之前建议进行文件备份。

4.使用 vi 等编辑器，根据服务器的规格，将最后一列数字改大，以提升限制值。或者将相关设置整个删除或注释（在最开头添加 # 号）整行配置：


 #* soft nofile 65535#* hard nofile 65535

5.使用 exit退出当前会话，然后从尝试客户端尝试重新连接。



**CentOS 6 之后版本操作系统**

对于 Cent OS（包含 RHEL）6.0之后版本操作系统，通过 /etc/security/limits.d/90-nproc.conf 进行全局资源控制。要解决该问题，请进行如下配置检查或修改：

1.通过 vnc 进入系统

2.使用 cat 等指令查看 /etc/security/limits.d/90-nproc.conf ，执行：


*cat /etc/security/limits.d/90-nproc.conf*

中是否包含类似如下设置：


    *   soft    nproc    65535

说明：

默认情况下，未启用上述配置。

第一列的 * 号，表示针对所有用户生效。也可以修改为指定的用户名，表示只对指定的用户生效。





3.如果需要修改相关配置，在继续之前建议进行文件备份。

4.使用 vi 等编辑器，根据服务器的规格，将最后一列数字改大，以提升限制值。或者将相关设置整个删除或注释（在最开头添加 # 号）整行配置：


 #*  soft    nproc    65535

5.使用 exit退出当前会话，然后从尝试客户端尝试重新连接。



如无法解决您的问题，请向我们提工单。

