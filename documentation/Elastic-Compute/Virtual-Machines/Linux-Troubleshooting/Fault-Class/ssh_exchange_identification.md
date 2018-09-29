# SSH 登录时出现如下错误：ssh_exchange_identification: read: Connection reset by peer




注意：本文相关 Linux 配置及说明已在 CentOS 6.5 64 位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。



**问题描述：**

当使用 SSH 登录Linux 云主机时，即便正确输入了密码，也会出现类似如下错误信息：

*ssh_exchange_identification: read: Connection reset by peer.*

*sshd[11949]: refused connect from 192.168.0.1 (192.168.0.1).*



**问题原因：**

该问题通常是由于 Linux 系统通过 /etc/hosts.allow 或 /etc/hosts.deny，启用了 TCP Wrapper  访问控制所致。



**解决办法：**

要解决此问题，请进行如下配置检查和修改：

1.通过 vnc 进入系统。

2.通过 cat 等指令查看 /etc/hosts.allow 或 /etc/hosts.deny中是否包含类似如下配置：


*all:all:deny*

3.如果需要修改相关策略配置，在继续之前建议进行文件备份。

4.使用 vi 等编辑器，按需修改 /etc/hosts.allow 和 /etc/hosts.deny中的相关配置，或者整个删除或注释（在最开头添加 # 号）整行配置。比如：


*# all:all:deny*

5.再次尝试登录服务器。



如无法解决您的问题，请向我们提工单。
