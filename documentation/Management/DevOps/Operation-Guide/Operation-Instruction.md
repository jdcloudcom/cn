# 使用须知

初次登录时，会默认创建示例服务树节点，如下：

![image](https://github.com/jdcloudcom/cn/blob/DevOps/image/DevOps/Operation-Guide1.png)

**登入操作**

地址：devops.jdcloud.com

![image](https://github.com/jdcloudcom/cn/blob/DevOps/image/DevOps/Operation-Guide2.png)

点击“京东云账户”进行登入

**安装超级Agent**

在云主机中，需安装超级Agent，用于部署和管理使用，安装Agent，具体方法如下

```
#华北-北京：
wget -c http://devops-hb.oss-internal.cn-north-1.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.377.8918eae.20180418132906.bin -O installer && sh installer /export/servers/ifrit && rm -f installer
#华东-上海：
wget -c http://devops-hd.oss-internal.cn-east-2.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.377.8918eae.20180418132906.bin -O installer && sh installer /export/servers/ifrit && rm -f installer
#华东-宿迁：
wget -c http://devops-sq.oss-internal.cn-east-1.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.377.8918eae.20180418132906.bin -O installer && sh installer /export/servers/ifrit && rm -f installer
#华南-广州：
wget -c http://devops.oss-internal.cn-south-1.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.377.8918eae.20180418132906.bin -O installer && sh installer /export/servers/ifrit && rm -f installer
```

在第三方主机（物理机or虚机）中，安装Agent的方法如下：

```
wget -c http://devops-hb.oss.cn-north-1.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.377.8918eae.20180418132906.bin -O installer && sh installer -- -t $tenant -r $region -v $vpc /export/servers/ifrit && rm -f installer
    -t tenant #devops中的租户名
    -v vpc    #由用户编写，将作为服务器的vpc名称
    -r region #由用户编写，将作为服务器的region名称
```

关于Agent的说明如下：

| 进程      |   说明  | 端口  |
| :--------: | :--------:| :--: |
| ifrit-agent  | 管理进程 |  1234 |
| ifrit-supervise  | 管理进程 |  |
| hawkeye-agent  | 用于监控 |  1235 |
| log-agent  | 用于日志采集 |   |
| zero-agent  | 控制系统agent ，用于部署、初始化、日志查询等 |   |


**登出操作**

点击右上角的头像，点击退出系统
