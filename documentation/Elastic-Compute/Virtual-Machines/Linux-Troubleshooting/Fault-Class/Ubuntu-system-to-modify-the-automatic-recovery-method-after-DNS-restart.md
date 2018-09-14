# Ubuntu系统修改DNS重启后自动还原的处理方法



**问题现象：**

ubuntu系统的云主机，修改 resolv.conf 文件中的DNS信息，重启云主机后， resolv.conf 文件中的信息会还原为修改前的信息；



**问题原因：**

ubuntu 系统中 /etc/resolv.conf 其实是一个软连接，如下图，文件软连到 /run/resolvconf/resolv.conf；

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%E7%B3%BB%E7%BB%9F%E4%BF%AE%E6%94%B9DNS%E9%87%8D%E5%90%AF%E5%90%8E%E8%87%AA%E5%8A%A8%E8%BF%98%E5%8E%9F%E7%9A%84%E5%A4%84%E7%90%86%E6%96%B9%E6%B3%9501.png)

**解决方法：**

可以直接修改 /run/resolvconf/resolv.conf文件中的DNS信息；

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%E7%B3%BB%E7%BB%9F%E4%BF%AE%E6%94%B9DNS%E9%87%8D%E5%90%AF%E5%90%8E%E8%87%AA%E5%8A%A8%E8%BF%98%E5%8E%9F%E7%9A%84%E5%A4%84%E7%90%86%E6%96%B9%E6%B3%9502.png)

如无法解决您的问题，请向我们提工单。
