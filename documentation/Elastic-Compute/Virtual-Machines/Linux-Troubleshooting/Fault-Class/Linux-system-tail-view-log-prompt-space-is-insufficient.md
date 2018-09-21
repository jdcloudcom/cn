# Linux系统tail查看日志提示空间不足

**问题现象：**

Linux主机 tail 查看日志时，提示空间不足，具体报错信息类似如下：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9Ftail%E6%9F%A5%E7%9C%8B%E6%97%A5%E5%BF%97%E6%8F%90%E7%A4%BA%E7%A9%BA%E9%97%B4%E4%B8%8D%E8%B6%B301.png)

**问题原因：**

tail 操作需要系统监控配额。同一用户同时添加的 watch 数目超出了内核 max_user_watches 参数配置，导致了该问题。



**处理办法：**

修改 /proc/sys/fs/inotify/max_user_watches 为较大值：

*sudo sysctl fs.inotify.max_user_watches=8192* # 以8192为例，此方式临时生效

如果想永久生效，需要修改/etc/sysctl.conf，添加 max_user_watches=8192，然后通过如下指令生效：

*sysctl -p*

如无法解决您的问题，请向我们提工单。
