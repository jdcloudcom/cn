# SSH连接断开超时设置



**问题现象：**

SSH连接登录云主机后，一段时间内如果不进行任何操作会自动断开。



**问题原因：**

SSH连接超时导致的。



**解决方法：**

登录云主机，对ssh配置文件进行编辑，输入命令：


*vi /etc/ssh/sshd_config*

找到ClientAliveInterval，这个参数是SSH连接维持的时间，数值是秒，可以自行设置。

例如：


*ClientAliveInterval 300*，表示300秒，即5分钟。


另外ClientAliveCountMax，这个参数是SSH允许超时的次数。如果客户端发现没有响应，则判断一次超时。

例如：


*ClientAliveCountMax 5*，表示允许超时5次。


如果进行如下设置，表示允许超时1500秒，即25分钟。

*ClientAliveInterval 300*

*ClientAliveCountMax 5*


如无法解决您的问题，请向我们提工单。
