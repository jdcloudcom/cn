# Windows系统cpu占用高排查
使用Windows时会遇到CPU高利用率的情况，在某些情况下这是正常的行为，例如客户购买了低规格(例如1核1G的云主机)安装了Windows 2012 服务器，有时会发现服务器的CPU突然飙高，定位下来发现是Windows Update服务在进行自动更新。但是在某些情况下，由于病毒木马，三方杀毒/网络防护软件，应用程序/驱动异常，运行高IO或者高中断处理的应用程序等情况下也会造成CPU占用率高。



如果希望快速解决问题，请尝试如下方法：

1.如果有安装杀毒软件，请检查CPU飙高时，杀毒软件是否在后台执行扫描操作。如果可能，请升级杀毒软件到最新版本，或者删除杀毒软件。

2.检查CPU飙高时，是否后台有执行Windows Update的行为。

3.运行Windows Update来安装最新的微软安全补丁。

4.如果该云主机内应用程序有大量的磁盘访问/网络访问行为/高计算需求，高CPU很可能是正常结果，您可以尝试增配实例规格的方式，使用更多核数/内存的规格来解决资源瓶颈问题。



**排查方式**

如果需要定位为何出现CPU高的原因，可以参考微软官方博客说明，微软有多个工具可以定位CPU高的问题，例如任务管理器，资源监视器，Process Explorer。



通过任务管理器，资源监视器来查看cpu的占用情况，以及查看占用cpu高的进程。

**windows2008系统查看方式：**

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Fcpu%E5%8D%A0%E7%94%A8%E9%AB%98%E6%8E%92%E6%9F%A501.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Fcpu%E5%8D%A0%E7%94%A8%E9%AB%98%E6%8E%92%E6%9F%A502.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Fcpu%E5%8D%A0%E7%94%A8%E9%AB%98%E6%8E%92%E6%9F%A503.png)

**windows2012系统查看方式：**

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Fcpu%E5%8D%A0%E7%94%A8%E9%AB%98%E6%8E%92%E6%9F%A504.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Fcpu%E5%8D%A0%E7%94%A8%E9%AB%98%E6%8E%92%E6%9F%A505.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Fcpu%E5%8D%A0%E7%94%A8%E9%AB%98%E6%8E%92%E6%9F%A506.png)

**通过Process Explorer工具查看方式：**

微软官方sysinternals工具，下载链接：https://technet.microsoft.com/en-us/sysinternals/processexplorer.aspx

该工具非常强大，在检查高CPU问题方面，通过配置正确的Symbols，可以通过检查对应应用程序的线程调用的Call Stack，来定位可能的问题驱动。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Fcpu%E5%8D%A0%E7%94%A8%E9%AB%98%E6%8E%92%E6%9F%A507.png)

如无法解决您的问题，请向我们提工单。
