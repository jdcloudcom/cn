# Windows重置winsock配置

如果遇到windows云主机的公网IP状态正常（无欠费、黑洞、肉鸡、封堵等异常），云主机安全组、ACL和系统自带防火墙没有限制，云主机可以获取内网IP，但是公网IP无法访问，或者在云主机内部无法访问公网的情况，有可能是winsock套接字配置异常导致，此时可以使用netsh winsock reset命令修复该问题。

**注意：在运行“netsh winsock reset”命令时，访问或监视 Internet 的程序（如防病毒程序、防火墙程序和代理客户端）可能会受到不良影响。如果使用此解决方案后您的某个程序不能正常工作，请重新安装该程序以恢复功能。**

**由于该操作存在一定风险性，建议您在操作前对您的云主机制作私有镜像（https://www.jdcloud.com/help/detail/312/isCatalog/1），以防止因重置操作导致的异常出现时无法恢复您的系统。**

netsh winsock reset命令，作用是重置 winsock 目录。如果一台机器上的winsock协议配置有问题的话将会导致网络连接等问题，就需要用netsh winsock reset命令来重置winsock目录借以恢复网络。这个命令可以重新初始化网络环境，以解决由于软件冲突、病毒等原因造成的参数错误问题。

重置方法如下：

同时按住windows徽标键和R键，打开运行对话框，在对话框中输出cmd，然后回车，启动CMD命令窗口，如图所示：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E9%87%8D%E7%BD%AEwinsock%E9%85%8D%E7%BD%AE01.png)

在CMD窗口中输入netsh winsock reset，按回车执行，执行成功后会提示成功地重置Winsock目录，需重启云主机生效，
如图所示：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E9%87%8D%E7%BD%AEwinsock%E9%85%8D%E7%BD%AE02.png)

重启云主机后验证云主机是否可以连通外网，如果仍不能解决您的问题，请提交工单。
