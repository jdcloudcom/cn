# Windows云主机自建SqlServer限制内存方法

在安装有SQLServer数据库的云主机上，我们在使用数据库的过程中，有时候会在任务管理器里发现sqlservr.exe这个进程的内存和CPU占用率较高。

通过设置SQL Server服务器中的最大服务器内存，可以解决使用数据库时占用系统内存过高的问题。

1、远程登陆云主机进入SqlServer数据库，选中数据库实例，然后鼠标右键，点击属性

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E4%BA%91%E4%B8%BB%E6%9C%BA%E8%87%AA%E5%BB%BASqlServer%E9%99%90%E5%88%B6%E5%86%85%E5%AD%98%E6%96%B9%E6%B3%9501.png)

点击内存选项卡，默认最大服务器内存非常大，我们这里一般限制为云主机内存的50%，例如16G内存*50%=8000MB.

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E4%BA%91%E4%B8%BB%E6%9C%BA%E8%87%AA%E5%BB%BASqlServer%E9%99%90%E5%88%B6%E5%86%85%E5%AD%98%E6%96%B9%E6%B3%9502.png)
