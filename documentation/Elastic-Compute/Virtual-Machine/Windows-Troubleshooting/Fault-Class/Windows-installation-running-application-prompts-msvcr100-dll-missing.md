# Windows安装运行应用程序提示msvcr100.dll丢失
**问题现象：**

Windows系统安装运行应用程序时，提示无法启动此程序，因为计算机丢失msvcr100.dll，如图：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E5%AE%89%E8%A3%85%E8%BF%90%E8%A1%8C%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F%E6%8F%90%E7%A4%BAmsvcr100.dll%E4%B8%A2%E5%A4%B101.png)

**问题原因：**

msvcr100.dll为Visual Studio 2010的一个动态链接库，如果某程序是用它开发出来的，那么该程序的运行就有可能需要此动态链接库。有些程序直接将其打包到了安装目录，并注册，就不会出现缺失的问题；但有些程序则默认系统中有此动态链接库，所以没有进行处理，因此就会出现缺失的问题



**解决方法：**

网络下载一个msvcr100.dll文件，一般是压缩包文件形式，下载后解压文件到相应目录即可。

1、如果下载的是32位MSVCR100.dll，系统也是32位，则复制到C:\Windows\System32目录下。如果是64位系统放到C:\Windows\SysWOW64。

2、如果下载的是64位MSVCR100.dll，系统是64位，则复制到C:\Windows\System32目录下。32位系统不兼容64位的MSVCR100.dll。

3、运行中输入*regsvr32 msvcr100.dll*，进行注册。



如无法解决您的问题，请向我们提工单。
