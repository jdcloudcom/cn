# 第三方镜像安全规范

1.系统组件安全
1.1基本要求
a)    不允许使用任何盗版或者破解版程序

b)   不允许存在任何木马后门、挂机、挖矿等恶意程序

c)    不允许存在已公开的、可利用的且已存在修复方案的安全漏洞

d)   不允许使用官方已经停止维护的发行版本，如Debina6、CentOS4、Win2003

e)    镜像制作时必须安装所有官方安全更新

f)     保证主机安全系统已安装并开机自启

1.2操作建议
安装安全更新：

a)    Windows：确保最新更新已安装

b)   Ubuntu：使用 apt update && apt upgrade 命令进行更新

c)    CentOS：使用 yum update 命令自动进行更新

检查主机安全防护状态：

a)    Windows：任务管理器 -> 进程，检查是否有jdcloudhids进程

b)   Linux：ps –ef | grep jdcloudhids，检查是否有jdcloudhids进程

1.3 重要组件安全
以下列出的组件必须保证无可被利用漏洞：

a)    引导、内核层面：grub、kernel、initramfs、sysvinit、systemd、efistub等

b)   运行依赖库：libc6、glibc、libssl（openssl）、libgnutls、OpenJDK、SunJDK、libtomcat、libxml、libgd、libpng、zlib、libpython、libnet、libkrb、libcup、libfuse、libdbus等

c)    常见用户态程序：openssh、sshfs、shell（bash、zsh、csh、dash…）、ftp、wget、curl、tar、gzip、sudo、su、ppp、rsync、fcitx、exim、apt、dpkg、rpm、yum、dnf等

2.第三方组件安全
2.1基本要求
a)    不允许存在已公开的、可利用的且已存在修复方案的安全漏洞

b)   不允许使用停止维护的软件版本系列，比如PHP 5.2、5.3、5.4、5.6系列，Mysql 5.1系列、  tomcat6及其以上版本

c)    镜像制作时，第三方组件请使用当时最新的稳定版本

d)   请通过官方渠道下载软件，切勿通过非官方站点下载，以防被植入后门

3.系统配置安全
4.1基本要求
a)    合理配置系统安全更新（镜像源的配置）

b)   禁止使用弱密码，请使用随机字符串作为各种程序的默认密码

c)    系统密码要有一定长度、复杂度要求（至少8位，包含大写字母、小写字母、特殊符号、数字）

d)   不允许出现非必须的SUID特权程序

e)    合理配置系统关键目录的权限，比如/etc、/bin、~/.ssh等

f)     除了/tmp目录，其他目录不允许出现777权限

g)   默认日志服务保证正常运行，如dmesg、syslog、wtmp、btmp、sudo等

h)   非公开服务端口不应用对外网开放（如redis 6379、mongodb 27017等），仅开放需要的

4.安全检测
4.1安全检测原则
a)    原则不允许存在已知公开修复方法的安全漏洞

b)   不上允许存在官方评级为“中危”以上的安全漏洞

c)    不允许存在可导致用户信息泄露、拒绝服务、服务崩溃、远程命令执行、获取主机控制权等安全漏洞

d)   应正确配置各类服务的访问权限，不允许出现如redis未授权访问、MongoDB弱口令等安全漏洞

e)    不允许存在来历不明的或ISV无法证明其它具体用途的程序

f)     不允许存在测试账户、测试数据等非生产环境必需的信息

g)   应清除配置镜像时产生的所有临时数据

h)   安全检测将对前述安全规范的执行情况进行检查，对于安全检测过程中发现的上述问题，将拒绝通过第三方镜像的安全检测环节，情节严重的将按照相关规定严肃追责
