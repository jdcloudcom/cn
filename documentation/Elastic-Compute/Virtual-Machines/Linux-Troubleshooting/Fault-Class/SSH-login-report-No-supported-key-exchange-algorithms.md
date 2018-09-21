# SSH登录报No supported key exchange algorithms




注意：本文相关 Linux 配置及说明已在 CentOS 6.5 64 位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。



**问题现象**


使用 SSH 连接 Linux 云主机时，客户端或服务端 secure 日志（可以通过 管理终端 进入系统查看）中可能会出现类似如下信息，导致无法正常连接服务器：

*• Read from socket failed: Connection reset by peer.*

*• Connection closed by 192.168.0.1.*

*• sshd error: could not load host key.*

*• fatal: No supported key exchange algorithms [preauth].*

*• DSA host key for 192.168.0.1 has changed and you have requested strict checking.*

*• Host key verification failed.*

*• ssh_exchange_identification: read: Connection reset by peer.*





**问题原因**

该问题通常是由于 SSH 服务相关的密钥文件异常所致，可能的原因包括：

• 相关密钥文件异常，比如文件损坏、被删除或篡改等。

• 相关密钥文件权限配置异常，导致无法正确读取。



**解决办法**

**方法一：检查文件权限**

SSH 服务会对相关密钥文件的权限进行检查。比如，私钥文件默认权限是 600，如果配置成 777 等其它权限，导致其它用户也有读取或修改权限。则 SSH 服务会认为该配置存在安全风险，进而导致客户端连接失败。

可以通过如下指令恢复相关文件的默认权限配置：


*cd /etc/ssh/*

*chmod 600 ssh_host_**

*chmod 644* *.pub*


操作示意如下：


*[root@centos]# cd /etc/ssh/*

*[root@centos]# chmod 600 ssh_host_**

*[root@centos]# chmod 644* *.pub*

*[root@centos]# ll*

*total 156*

*-rw-------. 1 root root 125811 Nov 23  2013 moduli*

*-rw-r--r--. 1 root root   2047 Nov 23  2013 ssh_config*

*-rw-------  1 root root   3639 May 16 11:43 sshd_config*

*-rw-------  1 root root    668 May 20 23:31 ssh_host_dsa_key*

*-rw-r--r--  1 root root    590 May 20 23:31 ssh_host_dsa_key.pub*

*-rw-------  1 root root    963 May 20 23:31 ssh_host_key*

*-rw-r--r--  1 root root    627 May 20 23:31 ssh_host_key.pub*

*-rw-------  1 root root   1675 May 20 23:31 ssh_host_rsa_key*

*-rw-r--r--  1 root root    382 May 20 23:31 ssh_host_rsa_key.pub*


**方法二：检查文件有效性**

如果参阅前述步骤，修改相关文件权限后，还是无法正常连接。由于 SSH 服务在启动时会自动重建丢失的密钥文件。所以，也可以直接将相关文件删除并重启 SSH 服务，让相关文件自动生成。

相关指令如下：

*cd /etc/ssh/*

*rm -rf ssh_host_**

*service sshd restart*


操作示意如下：


*[root@centos]# cd /etc/ssh/*

*[root@centos]# ll*

*total 156*

*-rw-------. 1 root root 125811 Nov 23  2013 moduli*

*-rw-r--r--. 1 root root   2047 Nov 23  2013 ssh_config*

*-rw-------  1 root root   3639 May 16 11:43 sshd_config*

*-rw-------  1 root root    672 May 20 23:08 ssh_host_dsa_key*

*-rw-r--r--  1 root root    590 May 20 23:08 ssh_host_dsa_key.pub*

*-rw-------  1 root root    963 May 20 23:08 ssh_host_key*

*-rw-r--r--  1 root root    627 May 20 23:08 ssh_host_key.pub*

*-rw-------  1 root root   1675 May 20 23:08 ssh_host_rsa_key*

*-rw-r--r--  1 root root    382 May 20 23:08 ssh_host_rsa_key.pub*

*[root@centos]# rm -rf ssh_host_**

*[root@centos]# ll*

*total 132*

*-rw-------. 1 root root 125811 Nov 23  2013 moduli*

*-rw-r--r--. 1 root root   2047 Nov 23  2013 ssh_config*

*-rw-------  1 root root   3639 May 16 11:43 sshd_config*

*[root@centos]# service sshd restart*

*Stopping sshd:                                             [  OK  ]*

*Generating SSH1 RSA host key:                              [  OK  ]*

*Generating SSH2 RSA host key:                              [  OK  ]*

*Generating SSH2 DSA host key:                              [  OK  ]*

*Starting sshd:                                             [  OK  ]*

*[root@centos]# ll*

*total 156*

*-rw-------. 1 root root 125811 Nov 23  2013 moduli*

*-rw-r--r--. 1 root root   2047 Nov 23  2013 ssh_config*

*-rw-------  1 root root   3639 May 16 11:43 sshd_config*

*-rw-------  1 root root    668 May 20 23:16 ssh_host_dsa_key*

*-rw-r--r--  1 root root    590 May 20 23:16 ssh_host_dsa_key.pub*

*-rw-------  1 root root    963 May 20 23:16 ssh_host_key*

*-rw-r--r--  1 root root    627 May 20 23:16 
ssh_host_key.pub*

*-rw-------  1 root root   1671 May 20 23:16 ssh_host_rsa_key*

*-rw-r--r--  1 root root    382 May 20 23:16 ssh_host_rsa_key.pub*


对于 Ubuntu 、Debain 类操作系统，修复指令如下：


*sudo rm -r /etc/ssh/ssh*key*

*sudo dpkg-reconfigure openssh-server*


如无法解决您的问题，请向我们提工单。
