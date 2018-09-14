# 设置云主机之间ssh免密码登录

ssh 免密码登录需要使用公钥与私钥。linux下可以用ssh-keygen生成公钥/私钥对，以CentOS为例。

现有云主机A(192.168.1.155)，云主机B(192.168.1.181)。现设置A机的user用户通过ssh免密码登录到B机的user用户。

如果是root用户设置免密登录，则将下述方法中的路径/home/user替换为/root即可，使用scp复制时也将目标机user替换为root即可。

1.在A机下生成公钥/私钥对。

*[user@A ~]$ ssh-keygen -t rsa*

出现交互界面要求输入密码、密钥保存路径等，均按回车以默认值生成即可
执行成功后在/home/user下生成.ssh目录，.ssh下有id_rsa和id_rsa.pub。

2.把A机下的id_rsa.pub复制到B机下相同路径下，使用scp命令，会要求输入B机user的登录密码，输入后回车即可完成复制

*[user@A ~]$ scp .ssh/id_rsa.pub user@192.168.1.181:/home/user/id_rsa.pub* 

*user@192.168.1.181's password:'s password:*

*id_rsa.pub                                    100%  223     0.2KB/s   00:00*


3.B机把从A机复制的id_rsa.pub添加到/home/user/.ssh/authorized_keys 文件里。

*[user@B ~]$ cat /home/user/id_rsa.pub >> /home/user/.ssh/authorized_keys*

*[user@B ~]$ chmod 600 /home/user/.ssh/authorized_keys*


authorized_keys的权限需设置为600。

4.A机登录B机。

*[user@A ~]$ ssh user@192.168.1.181*

*The authenticity of host 'B (192.168.1.181)' can't be established.*

*RSA key fingerprint is 00:a6:a8:87:eb:c7:40:10:39:cc:a0:eb:50:d9:6a:5b.*

*Are you sure you want to continue connecting (yes/no)? yes*

*Warning: Permanently added  '192.168.1.181' (RSA) to the list of known hosts.*

*Last login: Thu Mar 3 09:53:18 2018 from user*

*[user@B ~]$*



第一次登录时需要输入yes将B主机加入A主机的已知主机列表中

现在A机user用户可以无密码登录B机user用户了。

想让A，B机user用户无密码互相登录，在B机上以上述方法配置，将B机生成的id_rsa.pub内容添加至A机的authorized_keys文件中即可。

