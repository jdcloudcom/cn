# Linux系统cpu，内存高负载排查



注意：本文相关配置及说明已在 CentOS 6.5 64 位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。



**可以通过 top 从进程纬度来查看其 CPU、内存等资源的使用情况。**

用法说明：

*top*

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9Fcpu%EF%BC%8C%E5%86%85%E5%AD%98%E9%AB%98%E8%B4%9F%E8%BD%BD%E6%8E%92%E6%9F%A501.png)

回显说明：

默认界面上第三行会显示当前 CPU 资源的总体使用情况，下方会显示各个进程的资源占用情况。

可以直接在界面输入大小字母 P，来使监控结果按 CPU 使用率倒序排列，进而定位系统中占用 CPU 较高的进程。最后，根据系统日志和程序自身相关日志，对相应进程做进一步排查分析，以判断其占用过高 CPU 的原因。

**使用 top 直接终止 CPU 消耗较大的进程。**

如前面所述，可以通过 top 命令查看系统的负载问题，并定位耗用较多 CPU 资源的进程。可以直接在 top 运行界面快速终止相应的异常进程。说明如下：

1.想要终止某个进程，只需按下小写的 k 键。

2.输入想要终止的进程 PID （top 输出结果的第一列）。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9Fcpu%EF%BC%8C%E5%86%85%E5%AD%98%E9%AB%98%E8%B4%9F%E8%BD%BD%E6%8E%92%E6%9F%A502.png)

**CPU 使用率较低但负载较高**

问题描述：

Linux 系统没有业务程序运行，通过 top 观察，类似如下图所示，CPU 很空闲，但是 load average 却非常高。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9Fcpu%EF%BC%8C%E5%86%85%E5%AD%98%E9%AB%98%E8%B4%9F%E8%BD%BD%E6%8E%92%E6%9F%A503.png)

处理办法：

load average 是对 CPU 负载的评估，其值越高，说明其任务队列越长，处于等待执行的任务越多。出现此种情况时，可能是由于僵死进程导致的。可以通过指令 ps -axjf  查看是否存在 D 状态进程。D 状态是指不可中断的睡眠状态。该状态的进程无法被 kill，也无法自行退出。只能通过恢复其依赖的资源或者重启系统来解决。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9Fcpu%EF%BC%8C%E5%86%85%E5%AD%98%E9%AB%98%E8%B4%9F%E8%BD%BD%E6%8E%92%E6%9F%A504.png)

如无法解决您的问题，请向我们提工单。
