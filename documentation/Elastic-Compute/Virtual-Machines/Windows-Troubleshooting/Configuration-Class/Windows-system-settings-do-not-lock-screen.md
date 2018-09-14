# Windows系统设置不锁屏

以windows2012系统为例，通过控制台，远程连接vnc连接云主机，第一次登录需要输入ctrl+alt+delete进入系统。断开vnc，如果一段时间不登录，再次登录vnc后还是会提示让输入ctrl+alt+delete。可以尝试通过以下方式设置系统不锁屏。

1.左下角开始，选择运行。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E8%AE%BE%E7%BD%AE%E4%B8%8D%E9%94%81%E5%B1%8F01.png)

2.输入gpedit.msc，进入组策略配置界面。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E8%AE%BE%E7%BD%AE%E4%B8%8D%E9%94%81%E5%B1%8F02.png)

3.选择计算机配置--管理模版--控制面板--个性化，右侧选择不显示锁屏。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E8%AE%BE%E7%BD%AE%E4%B8%8D%E9%94%81%E5%B1%8F03.png)

4.选择已启用，应用。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E8%AE%BE%E7%BD%AE%E4%B8%8D%E9%94%81%E5%B1%8F04.png)

这样在退出vnc，再次连接vnc登录时就不会进入锁屏界面了。



如无法解决您的问题，请向我们提工单。
