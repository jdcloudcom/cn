# Windows2008限制系统缓存上限
MetaFile可以理解为系统缓存，Windows server 2008系统中，比如存在大量的文件拷贝等磁盘io操作，系统会自动将其缓存到内存中，这部分被占用的内存在任务管理器的中未体现出来的，所以用户会认为系统的内存占用异常。同时，MetaFile默认是没有限制的，所以系统会无限制占用内存。但是对于Windows 2012之后，操作系统会自动限制系统缓存的上限从而避免物理内存的耗尽。

微软官方Blog有一篇文章介绍因为MetaFile耗尽系统物理资源，通过Dyncache服务来解决此类问题，请注意该软件不适用于Windows 2012 之后的系统：

Troubleshooting Windows Performance Issues: Lots of RAM but no Available Memory



Microsoft Windows Dynamic Cache的更新程序，用户可以下载后添加到服务中，通过修改注册表来限制动态缓存的最大值，比如设置上限为200M等，这样系统就可以把作为缓存使用的内存设置了上限值。下载地址：

http://www.microsoft.com/en-us/download/details.aspx?id=9258 

具体设置步骤如下：

1.解压后根据不同系统版本中对应的DynCache.exe文件复制到C:\windows\system32中。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E9%99%90%E5%88%B6%E7%B3%BB%E7%BB%9F%E7%BC%93%E5%AD%98%E4%B8%8A%E9%99%9001.png)

2.以管理员身份打开命令提示符，执行如下命令添加服务：

***sc create DynCache binPath= %SystemRoot%\System32\DynCache.exe start= auto type= own DisplayName= "Dynamic Cache Service"***

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E9%99%90%E5%88%B6%E7%B3%BB%E7%BB%9F%E7%BC%93%E5%AD%98%E4%B8%8A%E9%99%9002.png)

3.回到DynCache文件夹，找到DynCache.reg的注册表文件导入（双击文件即可）。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E9%99%90%E5%88%B6%E7%B3%BB%E7%BB%9F%E7%BC%93%E5%AD%98%E4%B8%8A%E9%99%9003.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E9%99%90%E5%88%B6%E7%B3%BB%E7%BB%9F%E7%BC%93%E5%AD%98%E4%B8%8A%E9%99%9004.png)

4.运行输入regedit 打开注册表，找到*HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\DynCache\Parameters*。右侧找到*MaxSystemCacheMBytes*，双击它，这里我们选择“十进制”，在数值里输入要限制最大的缓存数（单位是MB），输入200就是限制缓存最大为200MB，输入0为不限制。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E9%99%90%E5%88%B6%E7%B3%BB%E7%BB%9F%E7%BC%93%E5%AD%98%E4%B8%8A%E9%99%9005.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E9%99%90%E5%88%B6%E7%B3%BB%E7%BB%9F%E7%BC%93%E5%AD%98%E4%B8%8A%E9%99%9006.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E9%99%90%E5%88%B6%E7%B3%BB%E7%BB%9F%E7%BC%93%E5%AD%98%E4%B8%8A%E9%99%9007.png)

5.运行输入*services.msc*，到服务中启动*DynCache*服务。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E9%99%90%E5%88%B6%E7%B3%BB%E7%BB%9F%E7%BC%93%E5%AD%98%E4%B8%8A%E9%99%9008.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E9%99%90%E5%88%B6%E7%B3%BB%E7%BB%9F%E7%BC%93%E5%AD%98%E4%B8%8A%E9%99%9009.png)

注：下载的dyncache解压出来是有多几个版本可选的，请选择retail amd64的版本，不要选择ia64（ia64表示安腾的64位处理器版本）。



如无法解决您的问题，请向我们提工单。

