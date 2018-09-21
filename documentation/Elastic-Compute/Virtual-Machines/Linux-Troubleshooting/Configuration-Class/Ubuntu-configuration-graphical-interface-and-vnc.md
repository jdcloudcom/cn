# Ubuntu配置图形界面和vnc

注意：本文相关 Linux 配置及说明已在 Ubuntu14.04 64位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。



**安装gnome桌面环境：**

1.安装x－windows的基础，执行以下命令：

*sudo apt-get -y install x-window-system-core*

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%E9%85%8D%E7%BD%AE%E5%9B%BE%E5%BD%A2%E7%95%8C%E9%9D%A2%E5%92%8Cvnc01.png)

2.安装登录管理器，执行以下命令：

*sudo apt-get -y install  gdm*

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%E9%85%8D%E7%BD%AE%E5%9B%BE%E5%BD%A2%E7%95%8C%E9%9D%A2%E5%92%8Cvnc02.png)

3.安装Ubuntu的桌面，执行以下命令：

*sudo apt-get -y install  ubuntu-desktop*

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%E9%85%8D%E7%BD%AE%E5%9B%BE%E5%BD%A2%E7%95%8C%E9%9D%A2%E5%92%8Cvnc03.png)

4.进入图形界面，执行以下命令：

*startx -extension GLX*

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%E9%85%8D%E7%BD%AE%E5%9B%BE%E5%BD%A2%E7%95%8C%E9%9D%A2%E5%92%8Cvnc04.png)

**安装配置vncserver服务：**

**安装**

执行命令

*apt-get -y install vnc4server*

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%E9%85%8D%E7%BD%AE%E5%9B%BE%E5%BD%A2%E7%95%8C%E9%9D%A2%E5%92%8Cvnc05.png)

**配置**

1.输入命令*vncserver* ，开启 vnc服务。首次启动会要求设置密码，后面可以使用 *vncpasswd* 修改

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%E9%85%8D%E7%BD%AE%E5%9B%BE%E5%BD%A2%E7%95%8C%E9%9D%A2%E5%92%8Cvnc06.png)

2.备份原有 xstartup 文件，执行命令：

*cp /root/.vnc/xstartup /root/.vnc/xstartup.bak*

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%E9%85%8D%E7%BD%AE%E5%9B%BE%E5%BD%A2%E7%95%8C%E9%9D%A2%E5%92%8Cvnc07.png)

3.修改vnc启动文件，使用以下命令：

*vi /root/.vnc/xstartup*

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%E9%85%8D%E7%BD%AE%E5%9B%BE%E5%BD%A2%E7%95%8C%E9%9D%A2%E5%92%8Cvnc08.png)

打开后如下图所示，把 x-window-manager &这一行注释掉，然后在下面加入一行 gnome-session &

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%E9%85%8D%E7%BD%AE%E5%9B%BE%E5%BD%A2%E7%95%8C%E9%9D%A2%E5%92%8Cvnc09.png)

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%E9%85%8D%E7%BD%AE%E5%9B%BE%E5%BD%A2%E7%95%8C%E9%9D%A2%E5%92%8Cvnc10.png)

4.杀掉原桌面进程，输入命令（其中的:1是桌面号），执行命令：

*vncserver -kill :1*

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%E9%85%8D%E7%BD%AE%E5%9B%BE%E5%BD%A2%E7%95%8C%E9%9D%A2%E5%92%8Cvnc11.png)

再次输入以下命令生成新的会话：

*vncserver :1*

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%E9%85%8D%E7%BD%AE%E5%9B%BE%E5%BD%A2%E7%95%8C%E9%9D%A2%E5%92%8Cvnc12.png)

5.设置vncserver开机自动启动，执行以下命令：

*vi /etc/rc.local*

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%E9%85%8D%E7%BD%AE%E5%9B%BE%E5%BD%A2%E7%95%8C%E9%9D%A2%E5%92%8Cvnc13.png)

添加vncserver启动命令 */usr/bin/vnc4server*

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%E9%85%8D%E7%BD%AE%E5%9B%BE%E5%BD%A2%E7%95%8C%E9%9D%A2%E5%92%8Cvnc14.png)

**测试登录**

客户端连接 ，完成前述配置后，在客户端安装 VNC Viewer 等 VNC 客户端，然后输入服务器的 IP 地址加 VNC 端口号（默认为 5901），进行 VNC 的连接：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/Ubuntu%E9%85%8D%E7%BD%AE%E5%9B%BE%E5%BD%A2%E7%95%8C%E9%9D%A2%E5%92%8Cvnc15.png)
