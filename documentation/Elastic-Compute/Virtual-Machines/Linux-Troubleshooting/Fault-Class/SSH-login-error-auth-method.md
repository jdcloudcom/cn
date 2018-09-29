# SSH 登录时出现如下错误：Disconnected:No supported authentication methods available



注意：本文相关 Linux 配置及说明已在 CentOS 6.5 64 位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。



**问题描述：**

当使用 SSH 登录 Linux 云主机时，即便正确输入了密码，也会出现类似如下错误信息：

*Permission denied (publickey,gssapi-keyex,gssapi-with-mic).*

*sshd[10826]: Connection closed by 192.168.0.1.*

*Disconnected:No supported authentication methods available.*

但相同用户，通过 vnc 可以正常登录。



问题原因：

该问题通常是由于 SSH 服务修改了 PasswordAuthentication 参数，禁用了密码验证登录所致。



处理办法：

1.通过 vnc 进入系统。

2.通过 cat 等指令查看 /etc/ssh/sshd_config中是否包含类似如下配置：


*cat /etc/ssh/sshd_config*

*PasswordAuthentication no*

说明：该参数默认启用，默认值为 yes。



3.如果需要修改相关策略配置，在继续之前建议进行文件备份。

4.使用 vi 等编辑器，将参数值设置为 yes，或者整个删除或注释（在最开头添加 # 号）整行配置：


*# PasswordAuthentication no*

5.使用如下指令重启 SSH 服务：


*service sshd restart*

6.再次尝试登录服务器。



如无法解决您的问题，请向我们提工单。
