# Windows系统内存占用分析
镜像：Windows Server 2008 R2 数据中心版 64位 中文版SQL Server 2008 R2 企业版 SP3 ，控制台看到内存占用即达到62%，相当于600多兆物理内存（1G内存规格）；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E5%86%85%E5%AD%98%E5%8D%A0%E7%94%A8%E5%88%86%E6%9E%9001.png)

登陆服务器系统，打开任务管理器，从进程占用这里看肯定是没有600多兆的；（内存大户mssql，这里看也不过39兆）如下图：
其实，任务管理器-进程这里看到的内存（专用工作集）内存占用，只是这个进程独占的物理内存；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E5%86%85%E5%AD%98%E5%8D%A0%E7%94%A8%E5%88%86%E6%9E%9002.png)

再打开系统自带资源管理器：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E5%86%85%E5%AD%98%E5%8D%A0%E7%94%A8%E5%88%86%E6%9E%9003.png)

这里的显示是准确的，物理内存的使用包含以下几个部分：
为硬件保留的内存
正在使用：由进程、驱动程序、操作系统使用的内存
已修改：内容必须写入磁盘才能用于其它用途的内存
备用：包含未使用的缓存数据和代码的内存
可用：不包含任何有价值数据，以及当进程、驱动程序、操作系统需要更多的内存时优先使用的内存
缓存：当文件被打开时，系统会把文件保存在缓存中，才以便下次迅速读写。Windows 2008 R2及以后，对这个缓存的使用也做了限制：有一部分物理内存不会被缓存使用，保证系统即使在缓存过大的时候，也有可用物理内存，满足程序使用需求。
看了这么多，还是没搞清楚除了进程占用的内存外，其他内存哪里去了。
好吧，请出终极工具：
名称：RamMap
版本：v1.0
主页：http://technet.microsoft.com/zh-cn/sysinternals/ff700229(en-us).aspx
作者：Windows Sysinternals

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E5%86%85%E5%AD%98%E5%8D%A0%E7%94%A8%E5%88%86%E6%9E%9004.png)

process private：进程正在使用的专有物理内存量；
paged pool：分页池
Mapped File内存映射文件
Nonpaged pool：非分页池
MetaFile：系统缓存 
可以看出，除了进程本身在占用物理内存外，Mapped File、paged pool、Nonpaged pool、MetaFile等等也都在占用内存，而任务管理器是看不到的；

我们再回到最开始的任务管理器，当勾选更多的监控列时，可以看到工作设置（内存）working set、内存（专用工作集）WS Private、提交大小（Private Bytes）

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E5%86%85%E5%AD%98%E5%8D%A0%E7%94%A8%E5%88%86%E6%9E%9005.png)

工作设置（内存）：进程正在使用的物理内存量；
内存（专用工作集）：该进程使用的而其他进程不能使用的物理内存；
提交大小：操作系统为进程保留的虚拟内存量；

工作设置内存 = 内存专用工作集 + 与其他进程共享的物理内存.
提交大小 = 内存专用工作集 + 保存在页面文件中的独占内存.

**因此，通过任务管理器的进程选项查看到的只是该进程本身占用的内存量，而windows系统本身在内存管理上是非常复杂的，除相关进程会占用内存外，Mapped File、paged pool、Nonpaged pool、MetaFile等等也都在占用内存，而任务管理器是看不到的。**
