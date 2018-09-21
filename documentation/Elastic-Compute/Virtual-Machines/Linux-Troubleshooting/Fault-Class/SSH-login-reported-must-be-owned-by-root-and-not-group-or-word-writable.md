# SSH登录报must be owned by root and not group or word-writable




注意：本文相关 Linux 配置及说明已在 CentOS 6.5 64 位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。



**问题现象**

Linux 云主机启动 SSH 服务时，出现类似如下错误信息：

*• /var/empty/sshd must be owned by root and not group or word-writable.*



**问题原因**

SSH 服务基于安全性考虑，对服务相关的目录或文件的权限配置、属组等都有要求。该问题通常是由于相关权限或属组设置异常所致。



**处理办法**

**方法一：/var/empty/sshd 目录配置**


/var/empty/sshd 目录权限默认为 711，默认属组为root:root。要解决此问题，请进行如下配置检查或修改：

1.通过 VNC 进入系统。

2.通过如下指令查看 /var/empty/sshd/ 目录的权限配置：


*ll -d /var/empty/sshd/*

默认配置：

*drwx--x--x. 2 root root 4096 Nov 23  2013 /var/empty/sshd/*



3.如果默认权限或属组被修改，则可以通过如下指令进行修改：


*chown -R root.root /var/empty/sshd* 

*chmod -R 711 /var/empty/sshd*


4.使用如下指令，重启 SSH 服务，验证服务可否正常启动：


*service sshd restart*


**方法二：/etc/securetty 目录配置问题**

/etc/securetty 目录权限配置默认为 600，默认属组为root:root。要解决此问题，请进行如下配置检查或修改：

1.通过 VNC 进入系统。

2.通过如下指令查看 /etc/securetty 目录的权限配置：


*ll /etc/securetty*

默认配置：

*-rw-------. 1 root root 122 Jan 12  2010 /etc/securetty*


3.如果默认权限或属组被修改，则可以通过如下指令进行修改：


*chown root.root /etc/securetty*

*chmod 600 /etc/securetty*


4.使用如下指令，重启 SSH 服务，验证服务可否正常启动：


*service sshd restart*


如无法解决您的问题，请向我们提工单。
