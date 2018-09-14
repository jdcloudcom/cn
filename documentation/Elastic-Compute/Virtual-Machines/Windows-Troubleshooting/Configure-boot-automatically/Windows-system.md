# Windows系统

sc命令
sc命令是Windows原生的服务控制命令，通过它可以方便地添加、删除标准的Windows服务程序：

#添加服务

*sc create ServiceName binpath= "D:\services\xxx.exe"*

#移除服务

*sc delete ServiceName*

请注意:

● binpath参数后面必须有一个空格

● 添加完服务后，需要自行配置一下，如将启动类型设置为“自动”

● 用户可以通过services.msc查看、管理已注册的服务

**添加自启动服务例子**

（1）在管理员权限下打开cmd，执行如下指令，将wosigncode.exe应用程序设置为服务程序

*sc create myservice binpath= "c:\wosigncode.exe"*

执行成功后见下图：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F01.png)

（2）运行-> 输入*services.msc*

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F02.png)

（3）找到刚才添加的服务myservice，单击右键，选择“属性”（见下图）

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F03.png)

（4）在启动类型中，选择“自动”，然后单击“启动”，最后单击“确定”即可完成该程序开机自启动设置。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F04.png)
