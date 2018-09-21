## 操作步骤

**1、获取登陆密码**

当您在云物理服务器控制台查看到购买到的服务器状态为【运行】时，说明已经安装好操作系统并交付给您了。登陆密码为您创建云物理服务器时所设置的密码，您也可在创建后登陆操作系统自行更改。

**2、获取外网IP**

请在控制台，找到刚刚购买的服务器，并找到外网IP地址。

**3、远程登陆**

下载远程链接软件Putty，参考下载地址：https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html.
打开Putty客户端，在PuTTY Configuration 窗口中输入以下内容：
- Host  Name：服务器的外网IP地址
-	Port：服务器的端口，必须填22。
-	Connect type：选择“SSH”。
-	全部输入完后，单击“Open”，创建一个新对话。

![PuTTY窗口](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS005.png)

在Putty会话窗口中， 输入管理员帐号，按回车键。
```
管理员帐号：
CentOS：root
Ubuntu：ubuntu
```
再输入初始密码，回车完成登录过程。

![PuTTY窗口](https://github.com/jdcloudcom/cn/blob/edit/image/Hyper-Converged-IDC/Cloud-Physical-Server/CPS006.png)

从本地Linux或Mac OS登录Linux云服务器，直接使用SSH命令进行连接，如：ssh root@Linux云服务器公网IP，然后输入root用户的初始密码，即可完成登录。

