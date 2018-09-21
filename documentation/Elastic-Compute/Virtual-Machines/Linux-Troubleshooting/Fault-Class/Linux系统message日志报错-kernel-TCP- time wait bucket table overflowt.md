# Linux系统message日志报错：kernel: TCP: time wait bucket table overflowt



**问题现象：**

云服务器 ECS ping 外部 IP 丢包，ping 出现错误：

*ping: sendmsg: Operation not permitted*

同时，查询服务器 /var/log/message 日志，发现大量类似如下错误信息：

*Aug  4 17:25:37 static1 kernel: TCP: time wait bucket table overflow Aug  4 17:25:37 static1 kernel: TCP: time wait bucket table overflow*

**问题原因：**

系统 TCP TIME WAIT溢出。



**解决办法：**

1.通过如下指令可以统计当前的 TCP 连接数：

*netstat -anp |grep tcp |wc -l*

2.对比 /etc/sysctl.conf 配置文件中参数 net.ipv4.tcp_max_tw_buckets 值，看是否有超出情况。

3.如果确认已经超出，则可以编辑 /etc/sysctl.conf 配置文件，根据系统规格，适当调大 net.ipv4.tcp_max_tw_buckets 参数值

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9Fmessage%E6%97%A5%E5%BF%97%E6%8A%A5%E9%94%99kernel01.png)

**说明：**

该参数并非支持无限调高，具体支持的调整值，和服务器的规格（带宽、CPU）有关。 

如果调高后，还是持续保持，则评估是否是正常业务流量。 如果是正常业务流量，则建议在服务器前端引入 负载均衡 等服务来进行流量分发，以降低单台服务器的流量负载。



如无法解决您的问题，请向我们提工单。
