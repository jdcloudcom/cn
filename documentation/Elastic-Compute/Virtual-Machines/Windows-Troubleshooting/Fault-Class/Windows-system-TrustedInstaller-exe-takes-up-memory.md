# Windows系统TrustedInstaller.exe占用内存高
**问题现象：**

资源监视器来查看TrustedInstaller.exe占用内存高，如图：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9FTrustedInstaller.exe%E5%8D%A0%E7%94%A8%E5%86%85%E5%AD%98%E9%AB%9801.png)

**问题原因：**

TrustedInstaller.exe实际上是“Windows Modules Installer”这个服务的进程，路径位于C:\Windows\servicing\TrustedInstaller.exe。当进行Windows Update，或者安装某些微软发布的安装包时，Windows Modules Installer服务会自动运行，导致进程持续消耗内存资源。



**解决方法：**

在服务中，将Windows Modules Installer 停止，设置为手动启动方式或者禁用。将Windows Update服务停止，设置为手动启动方式或者禁用即可。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9FTrustedInstaller.exe%E5%8D%A0%E7%94%A8%E5%86%85%E5%AD%98%E9%AB%9802.png)

如无法解决您的问题，请向我们提工单。
