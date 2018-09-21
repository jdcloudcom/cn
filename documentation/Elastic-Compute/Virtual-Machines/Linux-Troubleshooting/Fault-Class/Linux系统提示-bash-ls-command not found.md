# Linux系统提示-bash:ls:command not found



**问题现象：**

执行任何基本命令都提示command not found，如图：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9F%E6%8F%90%E7%A4%BA-bashlscommand%20not%20found01.png)

**问题原因：**

由于系统环境变量异常导致的。



**解决方法：**

永久生效方式：

更改为正确的环境变量，使用绝对命令vi打开/etc/profile


*vi  /etc/profile*

添加：


*export PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/root/bin*


临时生效方式：

直接执行


*export PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/root/bin*


如无法解决您的问题，请向我们提工单。
