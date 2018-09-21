# 如何从系统中查看服务器上一次被重启的时间

**1. 使用 last reboot 命令**

last 命令用于显示某个用户最近的登录记录。Linux 系统中，有一个名为 reboot 的伪用户，每次系统重启之后，该用户会自动登录系统。所以通过 last 命令检查 reboot 用户的登陆记录，其实就可以跟踪出系统的历史重启记录。其中括号中的信息表示系统上一次运行了多长时间，以及对应的时间段。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/%E5%A6%82%E4%BD%95%E4%BB%8E%E7%B3%BB%E7%BB%9F%E4%B8%AD%E6%9F%A5%E7%9C%8B%E6%9C%8D%E5%8A%A1%E5%99%A8%E4%B8%8A%E4%B8%80%E6%AC%A1%E8%A2%AB%E9%87%8D%E5%90%AF%E7%9A%84%E6%97%B6%E9%97%B401.png)

**2. 使用 who -b 命令**

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/%E5%A6%82%E4%BD%95%E4%BB%8E%E7%B3%BB%E7%BB%9F%E4%B8%AD%E6%9F%A5%E7%9C%8B%E6%9C%8D%E5%8A%A1%E5%99%A8%E4%B8%8A%E4%B8%80%E6%AC%A1%E8%A2%AB%E9%87%8D%E5%90%AF%E7%9A%84%E6%97%B6%E9%97%B402.png)

**3. 使用 uptime 命令**

uptime 命令可以显示系统当前时间，同时也会显示系统启动了多长时间，由此您可以推算出系统上一次启动的时间点。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/%E5%A6%82%E4%BD%95%E4%BB%8E%E7%B3%BB%E7%BB%9F%E4%B8%AD%E6%9F%A5%E7%9C%8B%E6%9C%8D%E5%8A%A1%E5%99%A8%E4%B8%8A%E4%B8%80%E6%AC%A1%E8%A2%AB%E9%87%8D%E5%90%AF%E7%9A%84%E6%97%B6%E9%97%B403.png)
