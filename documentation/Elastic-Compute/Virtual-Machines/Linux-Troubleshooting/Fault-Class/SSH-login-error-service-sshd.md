# SSH 登录时出现如下错误：pam_listfile(sshd:auth): Refused user root for service sshd



注意：本文相关 Linux 配置及说明已在 CentOS 6.5 64 位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。



**问题描述：**


登录 Linux 云主机时，即便输入了正确的密码，也无法正常登录。该问题出现时，控制台 vnc 或 SSH 客户端其中一种方式可以正常登录，或者两种方式均无法正常登录。同时，/var/log/secure 日志中出现类似如下错误信息：

*sshd[1199]: pam_listfile(sshd:auth): Refused user root for service sshd*

*sshd[1199]: Failed password for root from 192.168.0.1 port 22 ssh2*

*sshd[1204]: Connection closed by 192.168.0.2*



**问题原因：**

PAM 模块 pam_listfile.so 相关访问控制策略导致用户登录失败。



**处理方法：**

pam_listfile.so 模块可用于 Linux 访问控制。要解决此问题，请进行如下配置检查：

1.通过 SSH 客户端或 vnc 登录服务器。

2.通过 cat 等指令查看异常登录模式，对应的 PAM 配置文件。说明如下：

文件	功能说明

*/etc/pam.d/login*	控制台（vnc）对应配置文件

*/etc/pam.d/sshd*	登录对应配置文件

*/etc/pam.d/system-auth*	系统全局配置文件

注意：每个启用了 PAM 的应用程序，在 /etc/pam.d 目录中都有对应的同名配置文件。例如，login 命令的配置文件是 /etc/pam.d/login，可以在相应配置文件中配置具体的策略。



3.检查前述配置文件中，是否有类似如下配置信息：


*auth required pam_listfile.so item=user sense=allow file=/etc/ssh/whitelist onerr=fail*

相关参数简要说明：

item：设置访问控制的对象类型，可选值包括 tty|user|rhost|ruser|group|shell。

sense：定义了当在配置文件中找到符合条件的项目时的控制方式。可选值：allow|deny。即 allow 代表白名单方式，而 deny   代表黑名单方式。

file：用于指定配置文件的全路径名称。

onerr：定义了出现错误（比如无法打开配置文件）时的缺省返回值。



4.相关策略可以提高服务器的安全性。请用户基于安全性和易用性权衡后，再确定是否需要修改相关配置。

5.如果需要修改相关策略配置，在继续之前建议进行文件备份。

6.使用 vi 等编辑器，按需修改相关参数值，确认对应的访问控制文件中，已经对相应用户做了访问放行。或者整个删除或注释（在最开头添加 # 号）整行配置：


*#auth required pam_listfile.so item=user sense=allow file=/etc/ssh/whitelist onerr=fail*

7.尝试重新登录服务器。



如无法解决您的问题，请向我们提工单。
