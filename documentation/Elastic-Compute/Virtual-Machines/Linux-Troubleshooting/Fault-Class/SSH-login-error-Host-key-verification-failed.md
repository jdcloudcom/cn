# SSH登录报错Host key verification failed
注意：本文相关 Linux 配置及说明已在 CentOS 6.5 64 位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。

**问题描述：**

使用ssh 登录Linux系统云主机时，出现类似如下错误信息，导致无法正常连接。

 Linux 环境连接报错信息：

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!Someone could be eavesdropping on you right now (man-in-the-middle attack)!It is also possible that the RSA host key has just been changed.The fingerprint for the RSA key sent by the remote host isae:6e:68:4c:97:a6:91:81:11:38:8d:64:ff:92:13:50.Please contact your system administrator.Add correct host key in /root/.ssh/known_hosts to get rid of this message.Offending key in /root/.ssh/known_hosts:70RSA host key for x.x.x.x has changed and you have requested strict checking.Host key verification failed.

Windows 环境，以常见的 NetSarang Xshell 客户端为例，连接报错如下公钥指纹不匹配示意图所示： X.X.X.X （端口： XX）的主机密钥与本地主机密钥数据库中保存的不一致。主机密钥已更改或有人试图监听此连接。若无法确定，建议取消此连接。也可以在弹出相关告警信息的时候，直接点击 接收并保存 。让程序自动更新新密钥指纹信息，就可以继续正常登录。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/SSH%E7%99%BB%E5%BD%95%E6%8A%A5%E9%94%99Host%20key%20verification%20failed01.png)

**问题原因：**

Linux服务器系统重装、账户信息变更等致使其SSH 公钥变更，造成客户端保存公钥指纹与服务端不一致，导致 SSH 认证失败，拒绝登录。由于公钥一般较长（采用RSA算法时长达 1024 位）。所以，为了简便起见，通过对其MD5计算，生成一个128位的字符串用于信息对比。此称为公钥指纹。

**处理办法：**

客户端是 Windows 环境

1.打开Xshell程序。

2.单击 工具 > 主机密钥管理者，如下图所示，选中目标服务器对应条目，然后点击 删除 。

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/SSH%E7%99%BB%E5%BD%95%E6%8A%A5%E9%94%99Host%20key%20verification%20failed02.png)

3.重新登录服务器，确认保存新的公钥指纹后，即可成功登录。



客户端是 Linux 环境

1.使用 vi 等编辑器，编辑对应账户的 known_hosts 文件：

*vi ~/.ssh/known_hosts*

2.类似下图所示，找到对应条目，将其删除：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/SSH%E7%99%BB%E5%BD%95%E6%8A%A5%E9%94%99Host%20key%20verification%20failed03.png)

3.重新连接服务器，确认保存新的公钥指纹后，即可成功登录。



如无法解决您的问题，请向我们提工单。
