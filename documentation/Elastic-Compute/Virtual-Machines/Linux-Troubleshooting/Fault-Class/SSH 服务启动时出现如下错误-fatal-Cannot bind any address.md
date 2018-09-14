# SSH 服务启动时出现如下错误：fatal: Cannot bind any address




注意：本文相关 Linux 配置及说明已在 CentOS 6.5 64 位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。



**问题现象**


Linux 云主机启动 SSH 服务时，命令行或 secure日志出现类似如下错误信息：

*• FAILED.*

*• fatal: Cannot bind any address.*

*• ddress family must be specified before ListenAddress.*




**问题原因**

SSH 服务的 AddressFamily 参数用于指定运行时使用的协议簇。如果配置只使用了 IPV6，而系统内没有启用 IPV6、或 IPV6 协议没有得到有效配置，就可能会导致出现该问题。



**处理办法**

要解决该问题，请进行如下配置检查和修改：

1.通过 VNC 进入系统。

2.通过 cat 等指令查看 /etc/ssh/sshd_config 中是否包含类似如下配置：


*AddressFamily inet6*

说明：该参数可选值为：

• inet：使用 IPV4 协议簇，为默认值。

• net6：使用 IPV6 协议簇。

• any：同时启用 IPV4 和 IPV6 协议簇。



3.如果需要修改相关策略配置，在继续之前建议进行文件备份。

4.使用 vi 等编辑器，将参数值设置为 inet，或者整个删除或注释（在最开头添加 # 号）整行配置。比如：

*#AddressFamily inet6*

5.同时，确保 AddressFamily 参数在ListenAddress 之前配置，比如：


*AddressFamily any*   #该行配置在前面

*ListenAddress 0.0.0.0*


如无法解决您的问题，请向我们提工单。
