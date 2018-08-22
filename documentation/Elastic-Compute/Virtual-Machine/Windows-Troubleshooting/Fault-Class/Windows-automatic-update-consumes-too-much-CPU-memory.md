# Windows自动更新消耗cpu内存过高
**问题现象**

Windows默认如果开启了自动更新功能，会造成内存使用率过高或者CPU升高的情况。体现在svchost.exe这个进程占用内存很多，CPU有时候也会升高。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%87%AA%E5%8A%A8%E6%9B%B4%E6%96%B0%E6%B6%88%E8%80%97cpu%E5%86%85%E5%AD%98%E8%BF%87%E9%AB%9801.png)

**问题原因**

此进程消耗服务器资源主要有两种可能：

1、服务器被黑了存在木马病毒。

2、因为Windows自动更新功能没有关闭。如果服务器中没有异常木马病毒存在，通过关闭Windows Update功能即可解决。

**解决办法**

1.安装安全杀毒软件，进行查杀病毒。

2.禁用windows update自动更新。运行中输入gpedit.msc，在计算机配置，管理模板，windows update，配置自动更新，选择已禁用。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%87%AA%E5%8A%A8%E6%9B%B4%E6%96%B0%E6%B6%88%E8%80%97cpu%E5%86%85%E5%AD%98%E8%BF%87%E9%AB%9802.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%87%AA%E5%8A%A8%E6%9B%B4%E6%96%B0%E6%B6%88%E8%80%97cpu%E5%86%85%E5%AD%98%E8%BF%87%E9%AB%9803.png)

如无法解决您的问题，请向我们提工单。
