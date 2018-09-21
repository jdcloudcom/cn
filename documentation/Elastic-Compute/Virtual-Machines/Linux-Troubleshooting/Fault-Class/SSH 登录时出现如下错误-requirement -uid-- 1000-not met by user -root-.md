# SSH 登录时出现如下错误：requirement "uid >= 1000" not met by user "root"



注意：本文相关 Linux 配置及说明已在 CentOS 6.5 64 位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。



**问题描述：**

登录 Linux 云主机时，即便输入了正确的密码，也无法正常登录。该问题出现时，管理终端 或 SSH 客户端其中一种方式可以正常登录，或者两种方式均无法正常登录。同时，secure 日志中出现类似如下错误信息：

*pam_succeed_if(sshd:auth): requirement "uid >= 1000" not met by user "root".*



**问题原因：**

PAM 相关模块策略配置，禁止了 UID 小于 1000 的用户进行登录。



**处理方法：**


1.通过 SSH 客户端或 vnc 登录服务器。

2.通过 cat 等指令查看异常登录模式，对应的 PAM 配置文件。说明如下：

文件	功能说明

*/etc/pam.d/login*	控制台（vnc）对应配置文件

*/etc/pam.d/sshd*	登录对应配置文件

*/etc/pam.d/system-auth*	系统全局配置文件

注意：每个启用了 PAM 的应用程序，在 /etc/pam.d 目录中都有对应的同名配置文件。例如，login 命令的配置文件是 /etc/pam.d/login，可以在相应配置文件中配置具体的策略。



3.检查前述配置文件中，是否有类似如下配置信息：

*auth        required      pam_succeed_if.so uid >= 1000*

4.如果需要修改相关策略配置，在继续之前建议进行文件备份。

5.使用 vi 等编辑器，修改相应配置文件中的上述配置，或者整个删除或注释（在最开头添加 # 号）整行配置：

*auth        required      pam_succeed_if.so uid <= 1000* （修改）

或者

*#auth        required      pam_succeed_if.so uid >= 1000*（注释配置）

6.尝试重新登录服务器。



如无法解决您的问题，请向我们提工单。
