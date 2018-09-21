# FTP服务的安装与配置
使用云服务的过程中，我们经常遇到想要上传文件到主机中或者下载文件到本地的情况，这时我们需要用到FTP服务。



FTP 是File Transfer Protocol（文件传输协议）的英文简称，而中文简称为“文传协议”，用于Internet上的控制文件的双向传输。同时，它也是一个应用程序（Application）。基于不同的操作系统有不同的FTP应用程序，而所有这些应用程序都遵守同一种协议以传输文件。本文详细介绍CentOS系统环境下，如何部署和使用FTP服务来进行文件的上传和下载。



vsftpd是一款在Linux发行版中最受推崇的FTP服务器程序。特点是小巧轻快，安全易用。vsftpd 的名字代表”very secure FTP daemon”, 安全是它的开发者 Chris Evans 考虑的首要问题之一。在这个 FTP 服务器设计开发的最开始的时候，高安全性就是一个目标。

**一、安装前准备**

在京东云使用官方镜像CentOS 7.3 64位创建云主机，连接并以root身份登录云主机。

**二、安装FTP**

1、 使用yum命令安装vsftpd

*yum install vsftpd*

查看相关配置文件：

*cd /etc/vsftpd*

*ls*

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/FTP%E6%9C%8D%E5%8A%A1%E7%9A%84%E5%AE%89%E8%A3%85%E4%B8%8E%E9%85%8D%E7%BD%AE01.png)

*/etc/vsftpd/vsftpd.conf*     主配置文件，核心配置文件

*/etc/vsftpd/ftpusers*       黑名单，这个里面的用户不允许访问FTP服务器

*/etc/vsftpd/user_list*       白名单，允许访问FTP服务器的用户列表

2、 设置开机启动vsftpd ftp服务

*systemctl enable vsftpd.service*

3、启动vsftpd服务

*systemctl start vsftpd.service*

查看ftp服务端口:  
*netstat –antup | grep ftp*

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/FTP%E6%9C%8D%E5%8A%A1%E7%9A%84%E5%AE%89%E8%A3%85%E4%B8%8E%E9%85%8D%E7%BD%AE02.png)

登录ftp服务器：ftp://服务器ip地址:ftp端口(如果不填端口则默认访问21端口)

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/FTP%E6%9C%8D%E5%8A%A1%E7%9A%84%E5%AE%89%E8%A3%85%E4%B8%8E%E9%85%8D%E7%BD%AE03.png)

我们发现，这时候无需输入用户名密码即可登录FTP服务器。这是因为vsftpd安装后默认开启了匿名ftp的功能，用户无需额外配置即可使用匿名登录ftp服务器。这个时候任何用户都可以通过匿名方式登录ftp服务器，查看并下载匿名账户主目录下的各级目录和文件，但是不能上传文件或者创建目录。

匿名ftp的配置在*/etc/vsftpd/vsftpd.conf* 中设置：

*anonymous_enable=YES*     默认即为YES

**三、匿名ftp的其他设置**

出于安全方面的考虑，vsftpd在默认情况下不允许用户通过匿名FTP上传文件、创建目录等更改操作，但是可以修改vsftpd.conf配置文件的选项，可以赋予匿名ftp更多的权限。

1、允许匿名ftp上传文件：

修改/etc/vsftpd/vsftpd.conf

*write_enable=YES*

*anon_upload_enable=YES*

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/FTP%E6%9C%8D%E5%8A%A1%E7%9A%84%E5%AE%89%E8%A3%85%E4%B8%8E%E9%85%8D%E7%BD%AE04.png)

2、允许匿名修改ftp文件

更改/var/ftp/pub目录的权限，为ftp用户添加写权限，并重新加载配置文件

1）更改/var/ftp/pub目录的权限

*chmod o+w /var/ftp/pub/*

2）重启ftp服务

*systemctl restart vsftpd.service*

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/FTP%E6%9C%8D%E5%8A%A1%E7%9A%84%E5%AE%89%E8%A3%85%E4%B8%8E%E9%85%8D%E7%BD%AE05.png)

**四、配置本地用户登录**
vsftp安装后默只支持匿名ftp登录，用户如果试图使用Linux操作系统中的账号登录服务器，将会被vsftpd拒绝。本地用户登录就是指使用Linux操作系统中的用户账号和密码登录ftp服务器。

1、 创建本地用户：

*useradd ftptest*

*passwd ftptest*

需要输入两次密码

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/FTP%E6%9C%8D%E5%8A%A1%E7%9A%84%E5%AE%89%E8%A3%85%E4%B8%8E%E9%85%8D%E7%BD%AE06.png)

2、 修改vsftpd配置文件

打开配置文件：*vi /etc/vsftpd/vsftpd.conf*

在配置文件中修改如下代码：

*anonymous_enable=NO* (不允许匿名登陆)

*local_enble=yes* （本地帐户能够登陆）

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/FTP%E6%9C%8D%E5%8A%A1%E7%9A%84%E5%AE%89%E8%A3%85%E4%B8%8E%E9%85%8D%E7%BD%AE07.png)

同时，为保证后续客户端测试结果准确，推荐配置如下：

*local_umask=022* (FTP上本地的文件权限，默认是022)

*ftpd_banner=XXXXX* （欢迎信息）

*listen=NO* （独立的VSFTPD服务器，这里我设置成NO为了避免端口被占用等问题导致vsftpd无法打开）

*anon_upload_enable=NO* ( 不开放匿名上传权限)

*anon_mkdir_write_enable=yes* （不开放匿名新建文件夹权限）

*write_enable=yes* (开放本地用户写的权限)

3、 客户端测试

直接使用地址ftp://服务器ip地址:ftp端口(如果不填端口则默认访问21端口)，如图。弹出输入用户名和密码的对话框表示配置成功，正确的输入用户名和密码后，点击登录，即可对FTP文件进行相应权限的操作。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/FTP%E6%9C%8D%E5%8A%A1%E7%9A%84%E5%AE%89%E8%A3%85%E4%B8%8E%E9%85%8D%E7%BD%AE08.png)

如在ftp上新创建文件夹。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/FTP%E6%9C%8D%E5%8A%A1%E7%9A%84%E5%AE%89%E8%A3%85%E4%B8%8E%E9%85%8D%E7%BD%AE09.png)
