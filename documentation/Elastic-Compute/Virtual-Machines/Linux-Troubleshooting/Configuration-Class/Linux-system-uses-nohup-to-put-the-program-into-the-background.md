# Linux系统使用nohup将程序放至后台执行




有时候需要将一个命令放到后台执行，而不影响命令行的输入，同时用户登出也不会影响到该进程的执行，这个时候可以使用nohup及“&”功能。



Nohup的作用顾名思义，它使得后面的命令不会响应挂断（SIGHUP）信号，也就是说，在远程登录执行nohup后，即使退出登陆后，程序还是会正常执行。通常情况下，nohup命令最后会跟上“&”字符，表示将这个命令放至后台执行，这样才能真正做到将这个命令放至后台持续的执行。



使用举例：

1、正常的执行命令为*bash hello.sh*，执行结果为每秒输出一行的小程序：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9F%E4%BD%BF%E7%94%A8nohup%E5%B0%86%E7%A8%8B%E5%BA%8F%E6%94%BE%E8%87%B3%E5%90%8E%E5%8F%B0%E6%89%A7%E8%A1%8C01.png)

2、在命令头尾分别加上nohup和&，变为nohup bash hello.sh &，可以看到nohup输出了一行信息，再按一下回车键就跳回了shell命令行，此时命令已经在后台执行了，nohup将命令的输出重定向至当前目录的“nohup.out”文件中。同时注意到nohup会将对应程序的PID输出，这个PID可以记录一下，以便后续kill进程使用。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9F%E4%BD%BF%E7%94%A8nohup%E5%B0%86%E7%A8%8B%E5%BA%8F%E6%94%BE%E8%87%B3%E5%90%8E%E5%8F%B0%E6%89%A7%E8%A1%8C02.png)

3、通过*tail -f nohup.out*可以持续的查看nohup.out的输出，达到监视程序的效果。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Linux%E7%B3%BB%E7%BB%9F%E4%BD%BF%E7%94%A8nohup%E5%B0%86%E7%A8%8B%E5%BA%8F%E6%94%BE%E8%87%B3%E5%90%8E%E5%8F%B0%E6%89%A7%E8%A1%8C03.png)

4、在命令中也可以使用重定向将程序的输出改为自己想要的文件名，如*nohup bash hello.sh >hello.log &*，那么程序的输出就会写到hello.log文件中。



5、若程序不会自动退出，那么此时需要使用kill命令来杀死进程，可以使用命令*kill -TRM PID_NUMBER*来操作，其中PID_NUMBER就是之前nohup输出了值，在此例中该值为1231。



如无法解决您的问题，请向我们提工单。
