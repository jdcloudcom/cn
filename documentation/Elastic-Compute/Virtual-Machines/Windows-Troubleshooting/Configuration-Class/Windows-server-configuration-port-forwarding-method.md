# Windows服务器配置端口转发的方法
Windows服务器端口转发配置，可以使用Windows自带的portproxy功能实现，操作方法如下：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E6%9C%8D%E5%8A%A1%E5%99%A8%E9%85%8D%E7%BD%AE%E7%AB%AF%E5%8F%A3%E8%BD%AC%E5%8F%91%E7%9A%84%E6%96%B9%E6%B3%9501.png)

此命令的含义是：

使用ipv4 to ipv4模式将源地址是116.196.123.136的22端口代理到本服务器的所有地址的12345端口上，源地址处也可以改为可以内网互通的服务器的内网地址。

可以通过show all来查看已经添加的端口转发的配置信息：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E6%9C%8D%E5%8A%A1%E5%99%A8%E9%85%8D%E7%BD%AE%E7%AB%AF%E5%8F%A3%E8%BD%AC%E5%8F%91%E7%9A%84%E6%96%B9%E6%B3%9502.png)

端口转发配置完成后，直接访问本机的公网地址的12345端口，实际访问的是116.196.123.136服务器的22端口。



如果想删除配置的转发策略，可以使用如下命令删除下：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E6%9C%8D%E5%8A%A1%E5%99%A8%E9%85%8D%E7%BD%AE%E7%AB%AF%E5%8F%A3%E8%BD%AC%E5%8F%91%E7%9A%84%E6%96%B9%E6%B3%9503.png)
