# Linux系统ping测试总时间异常



**问题现象：**

ping 目标地址时延时都不高，但总时间却非常高。  比如，下图测试对京东云官网 ping 4 个包，每个包基本在 35ms 以内，但总体时间却经过 3000 多 ms，执行：

*ping www.jdcloud.com -c 4*

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9Fping%E6%B5%8B%E8%AF%95%E6%80%BB%E6%97%B6%E9%97%B4%E5%BC%82%E5%B8%B801.png)

**原因分析：**

实际这是由于每个 ping 包之间会间隔 1s 所致，所是正常的。



**处理办法：**

通过 -i 参数可以控制间隔时间。  比如，同样测试，通过指定 -i 0.1 参数后，可以看到总时间明显变小了。执行：

*ping www.jdcloud.com -c 4 -i 0.1*


![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9Fping%E6%B5%8B%E8%AF%95%E6%80%BB%E6%97%B6%E9%97%B4%E5%BC%82%E5%B8%B802.png)

如无法解决您的问题，请向我们提工单。
