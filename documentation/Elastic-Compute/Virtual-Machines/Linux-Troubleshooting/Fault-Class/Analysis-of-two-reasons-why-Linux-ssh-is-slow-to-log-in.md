# Linux ssh登陆慢的两种原因分析

Linux系统中/etc/ssh/sshd_config 下有两个参数可能会导致ssh连接慢，分别是UseDNS 和GSSAPIAuthentication，如遇到ssh登陆慢的问题，请参考如下操作：

编辑配置文件 /etc/ssh/sshd_config， vi /etc/ssh/sshd_config 找到 UseDNS选项，如果没有注释，将其注释 #UseDNS yes 添加 UseDNS no

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%20ssh%E7%99%BB%E9%99%86%E6%85%A2%E7%9A%84%E4%B8%A4%E7%A7%8D%E5%8E%9F%E5%9B%A0%E5%88%86%E6%9E%9001.png)

2、找到 GSSAPIAuthentication选项，如果没有注释，将其注释 #GSSAPIAuthentication yes 添加 GSSAPIAuthentication no

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%20ssh%E7%99%BB%E9%99%86%E6%85%A2%E7%9A%84%E4%B8%A4%E7%A7%8D%E5%8E%9F%E5%9B%A0%E5%88%86%E6%9E%9002.png)

3、保存配置文件



重启SSH服务 */etc/init.d/sshd restart*

注：如果客户端为Linux系统，需确保客户端做同样修改并重启生效。
