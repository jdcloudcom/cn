# 监控云数据库RDS  

## **安装监控插件**   
登录需要作为探测源的云主机（仅支持Linux主机），安装监控插件。具体步骤如下：  
1.根据云主机所在的地域，复制安装命令至云主机。  

地域 | 安装命令
------------|---------------------
华北-北京          | `wget -c http://devops-hb.oss-internal.cn-north-1.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.403.a81f9eb.20181127121007.bin -O installer && sh installer -- -a jcmagent /usr/local/share/jdcloud/ifrit && rm -f installer`  
华东-上海          | `wget -c http://devops-hd.oss-internal.cn-east-2.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.403.a81f9eb.20181127121007.bin -O installer && sh installer -- -a jcmagent /usr/local/share/jdcloud/ifrit && rm -f installer`  
华东-宿迁         | `wget -c http://devops-sq.oss-internal.cn-east-1.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.403.a81f9eb.20181127121007.bin -O installer && sh installer -- -a jcmagent /usr/local/share/jdcloud/ifrit && rm -f installer` 
华南-广州               | `wget -c http://devops.oss-internal.cn-south-1.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.403.a81f9eb.20181127121007.bin -O installer && sh installer -- -a jcmagent /usr/local/share/jdcloud/ifrit && rm -f installer` 

2.执行回车键，执行安装操作。等待1-3分钟，监控插件安装完成，可使用ps –ef | grep jcmagent 命令确认jcmagent进程，确保监控插件安装成功。  

## **创建监控任务**   
3.登录京东云云拨测控制台，点击“管理->云拨测->可用性监控”，进入可用性监控任务列表页面。点击左上角的“新建任务”按钮。  
4.填写配置信息
- 填写可用性监控的任务名称，例如：test_22  
- 选择探测源，选择已安装过监控插件且插件状态为“正常”的云主机。  
- 选择探测目标云数据库RDS，探测协议为TELNET，选择需要探测的数据库。  
5.点击确认，完成创建。该监控任务会根据选择的探测源持续探测数据的内网域名服务地址。  

## **查看监控图**  
6.上述任务添加成功后等待5-10分钟后，在可用性监控任务列表中，点击“监控图表”，即可查看到该任务在所选探测源对探测目标的响应时间及可用率。  

## **设置报警**    
7.返回至可用性监控任务列表，点击“报警规则”，进入到“报警规则”页面，点击“新增报警规则”，打开设置报警规则页面。  
8.选择监控项，例如：可用率、统计周期，例如5分钟、统计方法，例如：平均值、计算方法，例如小于，阈值，例如80%和持续周期，例如，持续2个周期，点击下一步设置通知方式，选择需要通知的联系人，点击下一步即可完成报警配置。  
注：报警服务会持续监测该RDS内网域名访问可用率指标，一旦达到报警阈值，则立即进行通知。

