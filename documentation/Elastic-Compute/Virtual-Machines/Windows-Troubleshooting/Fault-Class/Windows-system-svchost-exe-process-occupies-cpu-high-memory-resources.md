# Windows系统svchost.exe进程占用cpu，内存资源高的处理办法
**问题描述**

Windows系统内名为【svchost.exe】的进程，CPU或内存资源使用率一直居高不下，导致系统卡顿，影响正常使用。什么是 svchost.exe，svchost.exe 是计算机上的一个进程，该进程是Windows上用于执行各种功能的其它单独服务的宿主。可以有多个svchost.exe 的实例在计算机上运行，其中每个实例都包含不同的服务。svchost.exe 的一个实例可能有单个服务或多个服务。



**定位及解决办法**

使用任务管理器做简要分析，打开系统自带的【任务管理器】，快速判断出相应svchost进程下挂载的对应服务：

1.通过右键单击任务栏，然后单击“启动任务管理器”，打开“任务管理器”。

2.切换到“进程”选项卡。

3.单击“显示所有用户的进程”，若系统提示您输入管理员密码或进行确认，请键入该密码或提供确认。

4.右键单击资源使用过高的 svchost.exe实例，然后单击“转到服务”按钮，与进程关联的服务将在“服务”选项卡上突出显示。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Fsvchost.exe%E8%BF%9B%E7%A8%8B%E5%8D%A0%E7%94%A8cpu%EF%BC%8C%E5%86%85%E5%AD%98%E8%B5%84%E6%BA%90%E9%AB%98%E7%9A%84%E5%A4%84%E7%90%86%E5%8A%9E%E6%B3%9501.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Fsvchost.exe%E8%BF%9B%E7%A8%8B%E5%8D%A0%E7%94%A8cpu%EF%BC%8C%E5%86%85%E5%AD%98%E8%B5%84%E6%BA%90%E9%AB%98%E7%9A%84%E5%A4%84%E7%90%86%E5%8A%9E%E6%B3%9502.png)

使用SC Config命令隔离服务

在找到CPU占用高的Svchost之后，也可以尝试通过SC Config命令将svchost中驻存的服务“独立”出来到单独的svchost中运行：

1.客户遇到高CPU的情况，定位下来发现是svchost占用CPU较高。通过tasklist命令发现对应的svchost进程中有多个服务驻存。命令提示符下执行：***tasklist /svc***

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Fsvchost.exe%E8%BF%9B%E7%A8%8B%E5%8D%A0%E7%94%A8cpu%EF%BC%8C%E5%86%85%E5%AD%98%E8%B5%84%E6%BA%90%E9%AB%98%E7%9A%84%E5%A4%84%E7%90%86%E5%8A%9E%E6%B3%9503.png)

2.通过Sc config 命令我们可以将这些服务独立出来运行到单独的svchost进程中，例如：wuauserv（Windows Update服务）。命令提示符下执行：

***sc config wuauserv type= own***

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Fsvchost.exe%E8%BF%9B%E7%A8%8B%E5%8D%A0%E7%94%A8cpu%EF%BC%8C%E5%86%85%E5%AD%98%E8%B5%84%E6%BA%90%E9%AB%98%E7%9A%84%E5%A4%84%E7%90%86%E5%8A%9E%E6%B3%9504.png)

执行成功后重启服务器, 执行命令*tasklist /svc | findstr /I /C:wuau*，发现Windows Update服务已经成功独立。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Fsvchost.exe%E8%BF%9B%E7%A8%8B%E5%8D%A0%E7%94%A8cpu%EF%BC%8C%E5%86%85%E5%AD%98%E8%B5%84%E6%BA%90%E9%AB%98%E7%9A%84%E5%A4%84%E7%90%86%E5%8A%9E%E6%B3%9505.png)

3.经过监控发现确实是Windows Update的服务消耗CPU较高，后续响应的调整Windows Update策略晚上进行更新，避免工作时间影响服务器业务的运行。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Fsvchost.exe%E8%BF%9B%E7%A8%8B%E5%8D%A0%E7%94%A8cpu%EF%BC%8C%E5%86%85%E5%AD%98%E8%B5%84%E6%BA%90%E9%AB%98%E7%9A%84%E5%A4%84%E7%90%86%E5%8A%9E%E6%B3%9506.png)

如果恢复该服务与其它服务一起驻存到相同svchost中，请执行如下命令*sc config wuauserv type= share*，重启服务器生效。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Fsvchost.exe%E8%BF%9B%E7%A8%8B%E5%8D%A0%E7%94%A8cpu%EF%BC%8C%E5%86%85%E5%AD%98%E8%B5%84%E6%BA%90%E9%AB%98%E7%9A%84%E5%A4%84%E7%90%86%E5%8A%9E%E6%B3%9507.png)

如无法解决您的问题，请向我们提工单。
