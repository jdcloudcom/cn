# Centos安装配置vncserver
本文中仅讨论VNC的安装，关于图形界面需要您另行安装。



**CentOS 6.5 安装 VNC Server**

**安装**

使用以下命令安装vncserver：

*yum -y install tigervnc-server*

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver01.png)

**配置**

1.配置为开机自启动，使用以下命令将服务配置为开机自动启动：

*chkconfig --level 345 vncserver on*

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver02.png)

2.配置置客户端连接密码，输入以下命令后进行 VNC 密码的设置：

*vncserver*

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver03.png)

3.配置使用 GNOME 桌面，执行命令vi /root/.vnc/xstartup修改文件，把最后的 twm & 删除后，在添加以下内容：gnome-session &：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver04.png)

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver05.png)

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver06.png)

4.配置监听端口和环境参数，修改/etc/sysconfig/vncservers 文件，将最下方的两行配置注释，修改为以下内容：

*vncservers="1:root"*

*vncserverargs[1]="-geometry 1200x800"*

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver07.png)

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver08.png)

5.重启服务使配置生效，执行：

*service vncserver restart*

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver09.png)

**允许 root 访问图形界面和生成新的 machine-id**

执行以下命令：

*sed -i 's/.*!= root.*/#&/' /etc/pam.d/gdm*

*dbus-uuidgen >/var/lib/dbus/mechine-id*

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver10.png)


**关闭 selinux 和 NetworkManager 服务**

1.检查 selinux 服务并关闭，执行

*vi /etc/selinux/config*

确认里面的 SELINUX 字段的值是 disabled，如果不是则改为 disabled。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver11.png)

2.关闭 NetworkManager 服务，执行

*chkconfig --level 235 NetworkManager off*

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver12.png)

**测试登录成功**

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver13.png)

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver14.png)

**CentOS7 安装 VNC Server**

**安装**

使用以下命令安装vncserver：

*yum -y install tigervnc-server*

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver15.png)

**配置**

1.vi编辑配置文件，找到下面这几行，执行命令：

*vi /lib/systemd/system/vncserver@.service*

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver16.png)

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver17.png)

将Type更改为simple，用户名如果是root，那么<USER>就更改为root。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver18.png)

2.将 /lib/systemd/system/vncserver@.service 改为 /lib/systemd/system/vncserver@:1.service，执行命令：

*mv /lib/systemd/system/vncserver@.service /lib/systemd/system/vncserver@:1.service*

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver19.png)

3.重启 systemd，执行命令：

*systemctl daemon-reload*

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver20.png)

4.设置 VNC 密码，要设置某个用户的密码，必须要有能通过 sudo 切换到用户的权限。如果当前用户已经有 root 这里我用 root 的权限，执行“直接vncpasswd”就可以了。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver21.png)

5.设置开机启动：

*systemctl enable vncserver@:1.service*

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver22.png)

启动服务：

*systemctl start vncserver@:1.service*

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver23.png)

**测试登录**

客户端连接 ，完成前述配置后，在客户端安装 VNC Viewer 等 VNC 客户端，然后输入服务器的 IP 地址加 VNC 端口号（默认为 5901），进行 VNC 的连接：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/Centos%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEvncserver24.png)

如无法解决您的问题，请向我们提工单。
