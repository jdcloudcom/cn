# Linux系统修改主机名方法



修改Linux系统主机名常见的有两种方式，本文对此进行概要说明。



**临时生效修改**

使用命令行修改 hostname 主机名(可自定义)，重新登录 shell 生效。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9F%E4%BF%AE%E6%94%B9%E4%B8%BB%E6%9C%BA%E5%90%8D%E6%96%B9%E6%B3%9501.png)

重新登录 shell 后可以看到已经生效

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9F%E4%BF%AE%E6%94%B9%E4%B8%BB%E6%9C%BA%E5%90%8D%E6%96%B9%E6%B3%9502.png)

**永久生效修改**

以 CentOS 系统为例，需要更改配置文件生效，修改 /etc/sysconfig/network 里的 HOSTNAME=主机名(可自定义)，重启生效。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9F%E4%BF%AE%E6%94%B9%E4%B8%BB%E6%9C%BA%E5%90%8D%E6%96%B9%E6%B3%9503.png)

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9F%E4%BF%AE%E6%94%B9%E4%B8%BB%E6%9C%BA%E5%90%8D%E6%96%B9%E6%B3%9504.png)

如果是 Ubuntu 系统，则需要修改文件 /etc/hostname， 将其对应的主机名修改为新的主机名。

最后，需要将 /etc/hosts 中 127.0.0.1 对应的老主机名更换为新的主机名。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9F%E4%BF%AE%E6%94%B9%E4%B8%BB%E6%9C%BA%E5%90%8D%E6%96%B9%E6%B3%9505.png)

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9F%E4%BF%AE%E6%94%B9%E4%B8%BB%E6%9C%BA%E5%90%8D%E6%96%B9%E6%B3%9506.png)

注意：如果是 CentOS 7 操作系统，可以使用命令 hostnamectl set-hostname 主机名来修改，修改完毕后重新 SHELL 登录即可。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9F%E4%BF%AE%E6%94%B9%E4%B8%BB%E6%9C%BA%E5%90%8D%E6%96%B9%E6%B3%9507.png)

如无法解决您的问题，请向我们提工单。
