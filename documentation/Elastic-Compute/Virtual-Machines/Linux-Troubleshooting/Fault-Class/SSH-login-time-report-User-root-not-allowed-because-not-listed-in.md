# SSH登录时报User root not allowed because not listed in




注意：本文相关 Linux 配置及说明已在 CentOS 6.5 64 位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。



**问题现象**


使用 SSH 连接Linux 云主机时，客户端或服务端 secure 日志（可以通过 VNC 进入系统查看）中可能会出现类似如下信息，导致用户无法正常登录：

*• Permission denied, please try again.*

*• User test from 192.168.0.1 not allowed because not listed in AllowUsers.*

*• User test from 192.168.0.1 not allowed because listed in DenyUsers.*

*• User root from 192.168.0.1 not allowed because a group is listed in DenyGroups.*

*• User test from 192.168.0.1 not allowed because none of user's groups are listed in AllowGroups.*




**问题原因**

该问题通常是由于 SSH 服务启用了用户登录控制参数，对可登录用户进行限制所致。




**处理办法**

SSH 服务相关参数，可以对登录的用户或用户组进行限制。说明如下：

• AllowUsers：允许登录的用户白名单。只有该参数标注的用户可以登录。

• DenyUsers：拒绝登录的用户黑名单。该参数标注的用户都拒绝登录。

• AllowGroups：允许登录的用户组白名单。只有该参数标注的用户组可以登录。

• DenyGroups：拒绝登录的用户组黑名单。该参数标注的用户组都拒绝登录。



注意： 拒绝策略优先级高于允许策略。比如：

• 如果 AllowUsers 和 DenyUsers 参数包含了同一个用户，则拒绝策略优先，所以最终该用户还是无法登录。

• 如果 AllowUsers 和 DenyGroups 参数包含了同一个用户，则拒绝策略优先，所以最终该用户还是无法登录。



要解决此问题，对前述不同情况，请进行如下配置检查或修改：

1.通过 VNC 进入系统。

2.通过 cat 等指令查看 /etc/ssh/sshd_config 中是否包含类似如下配置：


*AllowUsers root test*

*DenyUsers test*

*DenyGroups test*

*llowGroups root*

3.如果需要修改相关策略配置，在继续之前建议进行文件备份。

4.使用 vi 等编辑器，修改策略配置，以确保相关用户能够正常登录。或者整个删除或注释（在最开头添加 # 号）整行配置（完全取消用户访问控制）：


*#AllowUsers root test*

*#DenyUsers test*

*#DenyGroups test*

*#AllowGroups root*

5.使用如下指令，重启 SSH 服务使配置生效：


*service sshd restart*


如无法解决您的问题，请向我们提工单。
