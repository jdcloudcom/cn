#Linux系统配置yum源和ntpd服务#

**一.配置yum源：**

**1.Centos7系统：**

执行*vi /etc/yum.repos.d/CentOS-Base.repo*
，将原有内容替换为如下内容：

[base]
name=CentOS-$releasever - Base - mirrors.jdcloudcs.com
baseurl=http://mirrors.jdcloudcs.com/centos/$releasever/os/$basearch/
gpgcheck=1
gpgkey=http://mirrors.jdcloudcs.com/centos/RPM-GPG-KEY-CentOS-7

[updates]
name=CentOS-$releasever - Updates - mirrors.jdcloudcs.com
baseurl=http://mirrors.jdcloudcs.com/centos/$releasever/updates/$basearch/
gpgcheck=1
gpgkey=http://mirrors.jdcloudcs.com/centos/RPM-GPG-KEY-CentOS-7

[extras]
name=CentOS-$releasever - Extras - mirrors.jdcloudcs.com
baseurl=http://mirrors.jdcloudcs.com/centos/$releasever/extras/$basearch/
gpgcheck=1
gpgkey=http://mirrors.jdcloudcs.com/centos/RPM-GPG-KEY-CentOS-7

[centosplus]
name=CentOS-$releasever - Plus - mirrors.jdcloudcs.com
baseurl=http://mirrors.jdcloudcs.com/centos/$releasever/centosplus/$basearch/
gpgcheck=1
enabled=0
gpgkey=http://mirrors.jdcloudcs.com/centos/RPM-GPG-KEY-CentOS-7

[contrib]
name=CentOS-$releasever - Contrib - mirrors.jdcloudcs.com
baseurl=http://mirrors.jdcloudcs.com/centos/$releasever/contrib/$basearch/
gpgcheck=1
enabled=0
gpgkey=http://mirrors.jdcloudcs.com/centos/RPM-GPG-KEY-CentOS-7

wq保存文件退出。

**2.Centos6系统：**

执行*vi /etc/yum.repos.d/CentOS-6.repo*
，将原有内容替换为如下内容：

[base]
name=CentOS-$releasever - Base - mirrors.jdcloudcs.com
baseurl=http://mirrors.jdcloudcs.com/centos/$releasever/os/$basearch/
gpgcheck=1
gpgkey=http://mirrors.jdcloudcs.com/centos/RPM-GPG-KEY-CentOS-6

[updates]
name=CentOS-$releasever - Updates - mirrors.jdcloudcs.com
baseurl=http://mirrors.jdcloudcs.com/centos/$releasever/updates/$basearch/
gpgcheck=1
gpgkey=http://mirrors.jdcloudcs.com/centos/RPM-GPG-KEY-CentOS-6

[extras]
name=CentOS-$releasever - Extras - mirrors.jdcloudcs.com
baseurl=http://mirrors.jdcloudcs.com/centos/$releasever/extras/$basearch/
gpgcheck=1
gpgkey=http://mirrors.jdcloudcs.com/centos/RPM-GPG-KEY-CentOS-6

[centosplus]
name=CentOS-$releasever - Plus - mirrors.jdcloudcs.com
baseurl=http://mirrors.jdcloudcs.com/centos/$releasever/centosplus/$basearch/
gpgcheck=1
enabled=0
gpgkey=http://mirrors.jdcloudcs.com/centos/RPM-GPG-KEY-CentOS-6

[contrib]
name=CentOS-$releasever - Contrib - mirrors.jdcloudcs.com
baseurl=http://mirrors.jdcloudcs.com/centos/$releasever/contrib/$basearch/
gpgcheck=1
enabled=0
gpgkey=http://mirrors.jdcloudcs.com/centos/RPM-GPG-KEY-CentOS-6

wq保存文件退出。

**3.Ubantu系统：**

执行*vi /etc/apt/sources.list*
，将原有内容替换为如下内容：

deb http://mirrors.jdcloudcs.com/ubuntu/ xenial main restricted

deb http://mirrors.jdcloudcs.com/ubuntu/ xenial-updates main restricted

deb http://mirrors.jdcloudcs.com/ubuntu/ xenial universe

deb http://mirrors.jdcloudcs.com/ubuntu/ xenial-updates universe

deb http://mirrors.jdcloudcs.com/ubuntu/ xenial multiverse

deb http://mirrors.jdcloudcs.com/ubuntu/ xenial-updates multiverse

deb http://mirrors.jdcloudcs.com/ubuntu/ xenial-backports main restricted universe multiverse

deb http://mirrors.jdcloudcs.com/ubuntu/ xenial-security main restricted

deb http://mirrors.jdcloudcs.com/ubuntu/ xenial-security universe

deb http://mirrors.jdcloudcs.com/ubuntu/ xenial-security multiverse

wq保存文件退出。

**二.配置ntpd服务：**

**1.调整ntpd配置文件：**

执行*vi /etc/ntp.conf*，将原有内容替换为如下内容：

driftfile /var/lib/ntp/drift

pidfile /var/run/ntpd.pid

logfile /var/log/ntp.log

#Access Control Support

restrict default kod nomodify notrap nopeer noquery

restrict -6 default kod nomodify notrap nopeer noquery

restrict 127.0.0.1

#local clock

server 127.127.1.0

fudge 127.127.1.0 stratum 10

#jdcloud ntp server

server ntp.jdcloudcs.com iburst minpoll 4 maxpoll 10

fudge ntp.jdcloudcs.com stratum 2

wq保存文件退出。

**2.启动ntpd服务：**

执行*services ntpd start*（Centos6系统）

执行*systemctl start ntpd*（Centos7系统）

执行*services ntpd start*（Ubantu系统）

**3.设置开机自启动服务：**

执行*chkconfig ntpd on*（Centos6系统）

执行*systemctl enable ntpd*（Centos7系统）

执行*chkconfig ntpd on*（Ubantu系统，需要先apt-get install chkconfig进行安装）
