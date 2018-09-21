# Windows Time_Wait过多导致访问外网失败
**问题现象：**

服务器内部可以ping通外网，但是无法访问外部的网站或者应用。

**问题原因：**

一般而言， 该问题原因是Windows动态端口耗尽。可以在CMD中输入如下命令简单测试：

***netstat -ano | findstr 445***

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%20Time_Wait%E8%BF%87%E5%A4%9A%E5%AF%BC%E8%87%B4%E8%AE%BF%E9%97%AE%E5%A4%96%E7%BD%91%E5%A4%B1%E8%B4%A501.png)

注：TCP 445端口是Windows文件共享服务使用端口，默认是监听状态。

执行

***telnet 127.0.0.1 445***

如果无法访问，说明动态端口耗尽。此时，如果使用netstat -ano命令，可以发现大量连接处于TIME_WAIT状态。

**解决办法：**

默认Windows 2008 以后，动态端口的数量为16384个 (从49152起始，到65536结束)，如果服务器对外有大量连接，而根据TCP默认的Time Wait Delay时间为4分钟，这会导致大量连接在断开后处于Time Wait状态，无法快速释放给其它连接使用，这可能导致端口耗尽。

1.增大动态端口数量

请以管理员身份打开CMD，运行如下命令：

***netsh int ipv4 set dynamicport tcp start=1025 num=60000***

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%20Time_Wait%E8%BF%87%E5%A4%9A%E5%AF%BC%E8%87%B4%E8%AE%BF%E9%97%AE%E5%A4%96%E7%BD%91%E5%A4%B1%E8%B4%A502.png)

该步骤无需重启机器, 立即生效。

2.降低Time Wait时间，最低为30秒

打开注册表，定位到HKLM\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters  新增键值 TcpTimedWaitDelay，类型REG_DWORD , 设置为十进制30，修改后重启生效。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%20Time_Wait%E8%BF%87%E5%A4%9A%E5%AF%BC%E8%87%B4%E8%AE%BF%E9%97%AE%E5%A4%96%E7%BD%91%E5%A4%B1%E8%B4%A503.png)

如无法解决您的问题，请向我们提工单。
