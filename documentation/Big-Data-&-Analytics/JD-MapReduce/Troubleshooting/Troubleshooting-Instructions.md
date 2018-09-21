# JMR问题排查说明

### 登录方式
JMR集群节点支持两种用户访问，Web界面登录和SSH登录。

- Web界面登录

1.JMR集群在创建完毕，默认启动Hadoop/Spark相关服务，您可以通过绑定的公网IP加服务端口，通过浏览器直接访问Hadoop相关服务的WebUI。
2.假设集群Master Web访问地址如下:
公网IP: 116.196.66.247
端口: 根据不同应用使用相应端口
常用应用访问入口:HDFS 
Web管理: 116.196.66.247:50070 
（目前只可访问22和8080端口，需求访问其他端口，请前往网络ACL设置）
3.JMR创建集群时默认为您创建并绑定了防火墙，如访问有问题，请检查
1)Master节点内网IP和公网IP是否绑定正确。
2)Hadoop/Spark等应用服务配置是否被修改，如修改请使用修改后的端口进行访问。 

- SSH登录 

1.JMR为集群的Master节点绑定了公网IP地址，通过SSH工具(如PuTTY)，您可以远程登录到服务器进行系统操作。
2.假设集群Master SSH访问地址如下:
公网IP: 116.196.66.247
端口: 22
登录账号: root
登录时使用您创建集群时设定的远程登录密码进行登录。 
3.JMR创建集群时默认为您创建并绑定了防火墙，如登录有问题，请检查。
1)Master节点内网IP和公网IP是否绑定正确。 
2)JMR默认防火墙策略是否被修改，如相应端口是否被修改。

###  常用命令
1.	执行以下命令切换用户
```
sudo su - hadoop
```
2.	查看节点运行的服务进程
```
[hadoop@OmkZafrH-Master1 ~]$ jps
9344 RunJar
6675 ApplicationHistoryServer
5028 QuorumPeerMain
5190 DFSZKFailoverController
4840 JournalNode
7386 HMaster
4765 Bootstrap
19757 Jps
8685 JobHistoryServer
9550 ResourceManager
5455 NameNode
10287 RunJar
```
3.	查看软件安装位置及软件目录
软件位置默认放在根目录的data0文件下
```
[hadoop@OmkZafrH-Master1 ~]$ cd /data0/
[hadoop@OmkZafrH-Master1 data0]$ ll
total 56
drwxr-xr-x  9 hadoop hadoop  4096 Oct 31 18:07 apache-hive-2.1.1-bin
drwxr-xr-x  6 root   root    4096 Apr 10 17:42 bdos
drwxr-xr-x  3 root   root    4096 Apr 10 17:41 bfd
drwxr-xr-x  5 root   root    4096 Apr 10 17:43 hadoop
drwxrwxrwx 11 hadoop hadoop  4096 Apr 10 17:42 hadoop-2.7.4
drwxr-xr-x  7 hadoop hadoop  4096 Oct 31 12:21 hbase-1.2.6
drwx------  2 root   root   16384 Apr 10 17:39 lost+found
drwxr-xr-x  4 root   root    4096 Apr 10 17:41 var
drwxr-xr-x  3 root   root    4096 Apr 10 17:43 yarn
drwxr-xr-x  3 hadoop hadoop  4096 Apr 10 17:42 zookeeper
drwxr-xr-x 10 hadoop hadoop  4096 Mar 23  2017 zookeeper-3.4.10
```
4.	查看环境变量
```
[hadoop@OmkZafrH-Master1 data0]$ vi ~/.bashrc 
# .bashrc

# Source global definitions
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi

# User specific aliases and functions

export HBASE_HOME=/data0/hbase-1.2.6
export PATH=$PATH:$HBASE_HOME/bin
export HBASE_HOME=/data0/hbase-1.2.6
export PATH=$PATH:$HBASE_HOME/bin
export HIVE_HOME=/data0/apache-hive-2.1.1-bin
export PATH=$PATH:$HIVE_HOME/bin
export HADOOP_HOME=/data0/hadoop-2.7.4
export PATH=$PATH:$HADOOP_HOME/bin
export HADOOP_LOG_DIR=/data0/var/log/hadoop
export HTTPFS_LOG=/data0/var/log/httpfs
export HADOOP_HOME=/data0/hadoop-2.7.4
export PATH=$PATH:$HADOOP_HOME/bin
export HADOOP_LOG_DIR=/data0/var/log/hadoop
export HTTPFS_LOG=/data0/var/log/httpfs
export ZOOKEEPER_HOME=/data0/zookeeper-3.4.10
export PATH=$PATH:$ZOOKEEPER_HOME/bin
export ZOO_LOG_DIR=/data0/var/log/zookeeper-3.4.10     
```

