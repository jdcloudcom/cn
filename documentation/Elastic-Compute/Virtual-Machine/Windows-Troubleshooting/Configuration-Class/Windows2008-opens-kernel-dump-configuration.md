# Windows2008开启内核转储配置
Windows默认没有开启内核转储（Core Dump）。某些特殊情况，比如蓝屏、卡死、hang机、黑屏等，需要借助Core Dump才能更快的定位问题根因，进而进行针对性的处理。



有2种方法可以配置，在微软官方 KB 都有提到：



如何在 Windows Server 2008 和 Windows Server 2008 R2 中生成内核或完全存储器转储文件：

https://support.microsoft.com/zh-cn/kb/969028

Troubleshoot “blue screen” or Stop error problems before you contact：

https://support.microsoft.com/kb/3106831



我们建议您采用手动配置工具方式，同时为防止配置问题导致系统启动失败和可能的数据丢失，请您务必对系统盘创建镜像，并且对数据盘创建快照备份后执行。

**手工配置 (适用所有版本Windows机器)**

1.右键计算机，选择属性。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/windows2008%E5%BC%80%E5%90%AF%E5%86%85%E6%A0%B8%E8%BD%AC%E5%82%A8%E9%85%8D%E7%BD%AE01.png)

2.选择高级系统设置。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/windows2008%E5%BC%80%E5%90%AF%E5%86%85%E6%A0%B8%E8%BD%AC%E5%82%A8%E9%85%8D%E7%BD%AE02.png)

3.系统属性选择高级，性能，设置。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/windows2008%E5%BC%80%E5%90%AF%E5%86%85%E6%A0%B8%E8%BD%AC%E5%82%A8%E9%85%8D%E7%BD%AE03.png)

4.性能选项选择高级，虚拟内存，更改。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/windows2008%E5%BC%80%E5%90%AF%E5%86%85%E6%A0%B8%E8%BD%AC%E5%82%A8%E9%85%8D%E7%BD%AE04.png)

5.将自动管理所有驱动器的分页文件大小勾选去掉，选择自定义大小。建议设置为“系统内存大小+1 MB ”即可。或者选择系统管理的大小，这样系统会优化分配分页文件。同时请确保系统盘有足够的剩余空间存储该页面文件以及后续生成的 Dump 文件。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/windows2008%E5%BC%80%E5%90%AF%E5%86%85%E6%A0%B8%E8%BD%AC%E5%82%A8%E9%85%8D%E7%BD%AE05.png)

6.系统属性选择高级，启动和故障恢复，设置。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/windows2008%E5%BC%80%E5%90%AF%E5%86%85%E6%A0%B8%E8%BD%AC%E5%82%A8%E9%85%8D%E7%BD%AE06.png)

7.写入调试信息，选择核心内存转储。转储文件默认保存在C:\MEMORY.DMP。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/windows2008%E5%BC%80%E5%90%AF%E5%86%85%E6%A0%B8%E8%BD%AC%E5%82%A8%E9%85%8D%E7%BD%AE07.png)

注意：如果 C 盘空间不足，建议可以将转储文件放到其它磁盘，例如 D:\memory.dmp。



如无法解决您的问题，请向我们提工单。
