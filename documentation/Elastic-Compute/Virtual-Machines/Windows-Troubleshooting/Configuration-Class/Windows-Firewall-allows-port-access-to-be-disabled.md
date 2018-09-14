# Windows防火墙允许禁止端口访问
注意：本文相关 Windows 配置及说明已在 Windows2012 64位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。

1.左下角点击开始，打开控制面板。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E9%98%B2%E7%81%AB%E5%A2%99%E5%85%81%E8%AE%B8%E7%A6%81%E6%AD%A2%E7%AB%AF%E5%8F%A3%E8%AE%BF%E9%97%AE01.png)

2.选择Windows防火墙，高级设置。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E9%98%B2%E7%81%AB%E5%A2%99%E5%85%81%E8%AE%B8%E7%A6%81%E6%AD%A2%E7%AB%AF%E5%8F%A3%E8%AE%BF%E9%97%AE02.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E9%98%B2%E7%81%AB%E5%A2%99%E5%85%81%E8%AE%B8%E7%A6%81%E6%AD%A2%E7%AB%AF%E5%8F%A3%E8%AE%BF%E9%97%AE03.png)

3.左侧栏选择入站规则，右侧栏选择新建规则。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E9%98%B2%E7%81%AB%E5%A2%99%E5%85%81%E8%AE%B8%E7%A6%81%E6%AD%A2%E7%AB%AF%E5%8F%A3%E8%AE%BF%E9%97%AE04.png)

4.选择端口，特定本地端口，填写需要允许/禁止的端口号。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E9%98%B2%E7%81%AB%E5%A2%99%E5%85%81%E8%AE%B8%E7%A6%81%E6%AD%A2%E7%AB%AF%E5%8F%A3%E8%AE%BF%E9%97%AE05.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E9%98%B2%E7%81%AB%E5%A2%99%E5%85%81%E8%AE%B8%E7%A6%81%E6%AD%A2%E7%AB%AF%E5%8F%A3%E8%AE%BF%E9%97%AE06.png)

5.选择允许或阻止连接策略，默认下一步。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E9%98%B2%E7%81%AB%E5%A2%99%E5%85%81%E8%AE%B8%E7%A6%81%E6%AD%A2%E7%AB%AF%E5%8F%A3%E8%AE%BF%E9%97%AE07.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E9%98%B2%E7%81%AB%E5%A2%99%E5%85%81%E8%AE%B8%E7%A6%81%E6%AD%A2%E7%AB%AF%E5%8F%A3%E8%AE%BF%E9%97%AE08.png)

6.为此规则填写名称，配置完成。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E9%98%B2%E7%81%AB%E5%A2%99%E5%85%81%E8%AE%B8%E7%A6%81%E6%AD%A2%E7%AB%AF%E5%8F%A3%E8%AE%BF%E9%97%AE09.png)

如无法解决您的问题，请向我们提工单。
