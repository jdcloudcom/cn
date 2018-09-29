# SSH 连接时出现如下错误：pam_unix(sshdsession) session closed for user



注意：本文相关 Linux 配置及说明已在 CentOS 6.5 64 位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。



**问题描述：**

当使用 SSH 登录 Linux 云主机时，即便正确输入了密码，在命令行或 secure 日志中也会出现类似如下错误信息，导致连接失败：

*This account is currently not available.*

*Connection to 127.0.0.1 closed.*

*Received disconnect from 127.0.0.1: 11: disconnected by user.*

*pam_unix(sshd:session): session closed for user test.*



**问题原因：**

该问题通常是由于相应用户的默认 Shell 被修改所致。



处理办法：

1.通过控制台 vnc 进入系统。

2.通过如下指令查看相应用户的默认 Shell：


*cat /etc/passwd | grep test*

*test: x :1000:1000::/home/test:/sbin/nologin*

查看相应用户的 Shell 是否被修改成了 nologin。



3.如果需要修改相关策略配置，在继续之前建议进行文件备份。

4.使用 vi 等编辑器，将相应用户的默认 Shell 修改为 bash比如：


*vi /etc/passwd*

将 /sbin/nologin 修改为 /bin/bash

5.从客户端再次尝试连接服务器。



如无法解决您的问题，请向我们提工单。
