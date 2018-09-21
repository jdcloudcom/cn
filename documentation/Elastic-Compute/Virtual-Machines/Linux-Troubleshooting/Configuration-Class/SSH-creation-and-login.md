# SSH创建和登录
对于Linux主机，SSH 服务可以对所有传输的数据进行加密，提供比传统 telnet 服务更高的安全性。而基于密钥认证的 SSH 自动化登录，在保障安全性的同时，可以简化登录过程，降低运维成本。本文主要对用户自己配置方法进行说明，京东云也在控制台提供密钥注入入口，请参考SSH密钥。

Linux系统云主机密钥配置
准备阶段需要用户登录云主机编辑云主机的配置文件，流程为“创建密钥”——“将公钥传入认证文件”——“配置密钥登录文件”——“重启密钥服务”。具体命令如下：

***yum install lrzsz/*** 安装上传下载工具

***ssh-keygen -t dsa -f ~/.ssh/JD/*** JD为密钥名称可以自定义

***Enter passphrase (empty for no passphrase):/*** 输入口令，也可以直接回车不设置口令

***Enter same passphrase again:***

***cd ~/.ssh***

***ls –l***

***cat JD.pub >>authorized_keys/*** 将公钥内容输出到相应文件中

***chmod 400 authorized_keys/*** 将文件属性设置为只读

***sz JD/*** 下载私钥到默认下载目录

***sz JD.pub/*** 下载公钥到默认下载目录

***rm –f ~/.ssh/JD.pub/*** 删除原来的公钥文件

***rm –f ~/.ssh/JD/*** 删除原来的私钥文件

***cd /etc/ssh***

***cp sshd_config sshd_configback/*** 备份ssh配置文件

***vi sshd_config/*** 编辑ssh配置文件

***PubkeyAuthentication yes/*** 开启密钥认证

***AuthorizedKeysfile .ssh/authorized_keys/*** PublicKey文件路径

***PasswordAuthentication no/*** 关闭密码认证（可选）

***#service sshd restart/*** 重启sshd服务

**用户登录**

1.Windows用户以SecureCRT登录为例。具体操作如下图：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/SSH%E5%88%9B%E5%BB%BA%E5%92%8C%E7%99%BB%E5%BD%9501.png)

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Linux/SSH%E5%88%9B%E5%BB%BA%E5%92%8C%E7%99%BB%E5%BD%9502.png)

2.Linux用户可直接通过命令登录。具体操作如下：

***ssh [–i path][-p port][user@hostname]***

例如:

***ssh -i /path/to/JD –p 22 root@192.168.0.1***

更多信息
Secure Shell：Wikipedia 上关于 SSH 的介绍和讨论。

https://en.wikipedia.org/wiki/Secure_Shell?spm=5176.7741493.0.0.dYU3RS

OpenSSH Manual Pages：OpenSSH 官方使用手册。

www.openssh.com/manual.html?spm=5176.7741493.0.0.dYU3RS

RSA：Wikipedia 上关于 RSA 算法的介绍。 

https://en.wikipedia.org/wiki/RSA_(cryptosystem)?spm=5176.7741492.0.0.K5YDOk

DSA：Wikipedia 上关于 DSA 算法的介绍。

https://en.wikipedia.org/wiki/Digital_Signature_Algorithm?spm=5176.7741492.0.0.K5YDOk
