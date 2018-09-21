# Linux系统查询时间同步服务器超时



**问题现象**

执行查看时间同步服务器命令报错，如图：

*ntpq -p*

*localhost: timed out, nothing received*

****Request timed out*

**问题原因**

ntp配置文件写的是调用ipv6地址执行会超时。

**解决办法**

**方法一.使用ipv4地址方式查询，执行：**

*ntpq -4p*

可以正确查询时间同步服务器，如图：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9F%E6%9F%A5%E8%AF%A2%E6%97%B6%E9%97%B4%E5%90%8C%E6%AD%A5%E6%9C%8D%E5%8A%A1%E5%99%A8%E8%B6%85%E6%97%B601.png)

**方法二.关闭ipv6地址，执行：**

*sh -c 'echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6'*

*ntpq -p*

查询结果如图：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9F%E6%9F%A5%E8%AF%A2%E6%97%B6%E9%97%B4%E5%90%8C%E6%AD%A5%E6%9C%8D%E5%8A%A1%E5%99%A8%E8%B6%85%E6%97%B602.png)

如无法解决您的问题，请向我们提工单。
