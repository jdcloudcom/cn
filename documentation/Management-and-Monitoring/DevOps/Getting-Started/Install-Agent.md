# 在云主机中安装超级Agent

在云主机中，需安装超级Agent，用于部署和管理使用，安装Agent，具体方法如下:

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

关于Agent的说明如下：

| 进程      |   说明  | 端口  |
| :--------: | :--------:| :--: |
| ifrit-agent  | 管理进程 |  1234 |
| ifrit-supervise  | 管理进程 |  |
| hawkeye-agent  | 用于监控 |  1235 |
| log-agent  | 用于日志采集 |   |
| zero-agent  | 控制系统agent ，用于部署、初始化、日志查询等 |   |
