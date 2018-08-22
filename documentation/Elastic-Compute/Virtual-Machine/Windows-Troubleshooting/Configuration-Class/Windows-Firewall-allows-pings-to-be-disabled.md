# Windows防火墙允许禁止ping
注意：本文相关 Windows 配置及说明已在 Windows2012 64位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。

1.左下角点击开始，打开控制面板。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E9%98%B2%E7%81%AB%E5%A2%99%E5%85%81%E8%AE%B8%E7%A6%81%E6%AD%A2ping01.png)

2.选择Windows防火墙，高级设置。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E9%98%B2%E7%81%AB%E5%A2%99%E5%85%81%E8%AE%B8%E7%A6%81%E6%AD%A2ping02.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E9%98%B2%E7%81%AB%E5%A2%99%E5%85%81%E8%AE%B8%E7%A6%81%E6%AD%A2ping03.png)

3.左侧栏选择入站规则，中间栏双击选择文件和打印机共享（回显请求 - ICMPv4-In）。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E9%98%B2%E7%81%AB%E5%A2%99%E5%85%81%E8%AE%B8%E7%A6%81%E6%AD%A2ping04.png)

4.常规，操作，选择允许/阻止连接，来设置允许/禁止ping，确定即可生效。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E9%98%B2%E7%81%AB%E5%A2%99%E5%85%81%E8%AE%B8%E7%A6%81%E6%AD%A2ping05.png)

如无法解决您的问题，请向我们提工单。
