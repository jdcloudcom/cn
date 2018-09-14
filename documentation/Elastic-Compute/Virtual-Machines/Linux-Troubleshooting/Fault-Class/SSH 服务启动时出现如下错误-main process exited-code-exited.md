# SSH 服务启动时出现如下错误：main process exited, code=exited




注意：本文相关 Linux 配置及说明已在 CentOS 6.5 64 位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。



**问题描述：**

Linux 云主机使用 service 或 systemctl 指令启动 SSH 服务时，命令行没有任何报错信息。但服务实际没有正常运行，同时在 secure 日志出现类似如下错误信息：

*• sshd.service: main process exited, code=exited, status=203/EXEC.*

*• init: ssh main process (1843) terminated with status 255.*



**问题原因：**

该问题通常是由于 $PATH 环境变量配置异常，或 SSH 服务相关指令被移除，导致服务启动脚本无法正常运行所致。



**解决办法：**


要解决该问题，请进行如下配置检查或修改：

1.通过 vnc 进入系统。

2.使用如下指令检查环境变量配置：


*echo $PATH*

默认值如下：

*/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/root/bin*


3.如果默认环境变量被改变，则通过如下指令重置：



*export PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/root/bin*


4.使用如下指令查找并确认 SSH 服务指令：

*find / -name sshd*

确保包含如下默认路径程序文件：

*/usr/sbin/sshd*


5.如果相应文件不存在，则尝试通过 FTP 等方式从外部上传正常文件，或者重新安装 SSH 服务。

6.使用如下指令重启 SSH 服务，然后从客户端尝试重新连接：

*service sshd restart*


如无法解决您的问题，请向我们提工单。
