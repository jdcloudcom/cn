# 使用可用性监控

**安装监控插件**  

登录需要作为探测源的云主机（仅支持Linux主机），安装监控插件。具体步骤如下：  
1.配置credential文件  
  - 创建~/.jdcloud/monitor_credentials.yml文件  
  - 编缉并保存monitor_credentials.yml文件，文件内容为：  
  ```
   ak: xxxxxxx(填写YourAccessKeyID)   
   sk: xxxxxxx(填写YourAccessKeySecret) 
   ```
   注： ak\sk内容填写须符合yaml语法（键值对之间必须要有空格），否则会读取ak\sk失败。如: ak:(空格)xxxxxx

2.根据云主机所在的地域，复制安装命令至云主机。  

地域 | 安装命令
------------|---------------------
华北-北京          | `wget -c http://devops-hb.oss-internal.cn-north-1.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.403.a81f9eb.20181127121007.bin -O installer && sh installer -- -a jcmagent /usr/local/share/jdcloud/ifrit && rm -f installer`  
华东-上海          | `wget -c http://devops-hd.oss-internal.cn-east-2.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.403.a81f9eb.20181127121007.bin -O installer && sh installer -- -a jcmagent /usr/local/share/jdcloud/ifrit && rm -f installer`  
华东-宿迁         | `wget -c http://devops-sq.oss-internal.cn-east-1.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.403.a81f9eb.20181127121007.bin -O installer && sh installer -- -a jcmagent /usr/local/share/jdcloud/ifrit && rm -f installer` 
华南-广州               | `wget -c http://devops.oss-internal.cn-south-1.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.403.a81f9eb.20181127121007.bin -O installer && sh installer -- -a jcmagent /usr/local/share/jdcloud/ifrit && rm -f installer`  

3.执行回车键，执行安装操作。等待1-3分钟，监控插件安装完成，可使用ps –ef | grep jcmagent 命令确认jcmagent进程，确保监控插件安装成功。  

   

**创建监控任务**   

4.登录京东云云拨测控制台，点击“管理->云拨测->可用性监控”，进入可用性监控任务列表页面。点击左上角的“新建任务”按钮。  
5.填写配置信息
- 填写可用性监控的任务名称；
- 选择探测源，选择已安装过监控插件且插件状态为“正常”的云主机
- 选择探测目标URL/IP，探测协议为HTTP(S)，输入探测目标，例如console.jdcloud.com  

6.点击确认，完成创建。

**查看监控图**  

7.上述任务添加成功后等待5-10分钟后，在可用性监控任务列表中，点击“监控图表”，即可查看到该任务在所选探测源对探测目标的响应时间及可用率。  

**设置报警**  

8.返回至可用性监控任务列表，点击“报警规则”，进入到“报警规则”页面，点击“新增报警规则”，打开设置报警规则页面。  
9.选择监控项、统计周期、统计方法、计算方法，阈值和持续周期，点击下一步设置通知方式，选择需要通知的联系人，点击下一步即可完成报警配置。
