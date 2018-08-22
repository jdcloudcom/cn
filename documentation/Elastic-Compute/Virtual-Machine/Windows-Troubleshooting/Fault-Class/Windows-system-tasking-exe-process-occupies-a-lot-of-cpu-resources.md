# Windows系统tasking.exe进程占用大量cpu资源
**问题现象：**

任务管理器中查看tasking.exe进程占用大量cpu资源，结束进程树后会自动再开启，删除文件也没有用。如图：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Ftasking.exe%E8%BF%9B%E7%A8%8B%E5%8D%A0%E7%94%A8%E5%A4%A7%E9%87%8Fcpu%E8%B5%84%E6%BA%9001.png)

**问题原因：**

National Instruments Domain Service启动运行形成的进程导致。



**解决办法：**

首先是在运行中输入*msconfig*，常规设置里改成有选择的启动，点进服务，先点一下左下角隐藏Microsoft服务，从剩下的服务中找到名为National Instruments Domain Service的一条，把它前面的勾去掉然后应用，重启服务器生效。如图：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Ftasking.exe%E8%BF%9B%E7%A8%8B%E5%8D%A0%E7%94%A8%E5%A4%A7%E9%87%8Fcpu%E8%B5%84%E6%BA%9002.png)

如无法解决您的问题，请向我们提工单。
