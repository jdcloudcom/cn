## 安装可用性监控插件

### 1.登录作为探测源的京东云Linux云主机。

![](https://raw.githubusercontent.com/jdcloudcom/cn/edit/image/Cloud-Monitor/Usability-Monitor/agent1.jpg)

### 2. 配置credential文件    
  - 创建~/.jdcloud/monitor_credentials.yml文件   
  - 编缉并保存monitor_credentials.yml文件，文件内容为：  

   ```
   ak: xxxxxxx(填写YourAccessKeyID)   
   sk: xxxxxxx(填写YourAccessKeySecret) 
   ```  
   注：ak\sk内容填写须符合yaml语法（键值对之间必须要有空格），否则会读取ak\sk失败。如: ak:(空格)xxxxxx
### 3.根据云主机所在地域，复制安装命令至云主机上。

地域 | 安装命令
-- |--
**华北-北京** | `wget -c http://devops-hb.oss-internal.cn-north-1.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.403.a81f9eb.20181127121007.bin -O installer && sh installer -- -a jcmagent /usr/local/share/jdcloud/ifrit && rm -f installer`
**华东-上海** | `wget -c http://devops-hd.oss-internal.cn-east-2.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.403.a81f9eb.20181127121007.bin -O installer && sh installer  -- -a jcmagent /usr/local/share/jdcloud/ifrit && rm -f installer`
**华东-宿迁** | `wget -c http://devops-sq.oss-internal.cn-east-1.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.403.a81f9eb.20181127121007.bin -O installer && sh installer -- -a jcmagent /usr/local/share/jdcloud/ifrit && rm -f installer`
**华南-广州** | `wget -c http://devops.oss-internal.cn-south-1.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.403.a81f9eb.20181127121007.bin -O installer && sh installer -- -a jcmagent  /usr/local/share/jdcloud/ifrit && rm -f installer`

![](https://raw.githubusercontent.com/jdcloudcom/cn/monitoring/image/Cloud-Monitor/Usability-Monitor/agent2.jpg)

### 4.点击回车，执行安装命令。

![](https://raw.githubusercontent.com/jdcloudcom/cn/edit/image/Cloud-Monitor/Usability-Monitor/agent3.jpg)

### 5. 执行安装命令后，等待1-3分钟使用ps -ef|grep jcmagent 命令确认jcmagent进程是否启动。

![](https://raw.githubusercontent.com/jdcloudcom/cn/edit/image/Cloud-Monitor/Usability-Monitor/agent4.jpg)

### 5.如安装失败，1-3分钟后重新执行安装命令。多次失败，请联系客服。
