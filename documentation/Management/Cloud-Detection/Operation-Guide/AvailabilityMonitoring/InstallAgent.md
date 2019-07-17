# 安装监控插件
选择需要作为探测源的云主机（仅支持Linux类主机），登录该云主机。  
1. 配置credential文件  
  - 创建 ~/.jdc/monitor_credentials.yml 文件  
  - 编缉并保存monitor_credentials.yml文件，文件内容为：  
   ```
   ak: xxxxxxx(填写YourAccessKeyID)   
   sk: xxxxxxx(填写YourAccessKeySecret) 
   ```
   注： ak\sk内容填写须符合yaml语法（键值对之间必须要有空格），否则会读取ak\sk失败。如: ak:(空格)xxxxxx

2. 根据该云主机所在地域，复制以下命令至云主机。  

地域 | 安装命令
------------|---------------------
华北-北京          | `wget -c http://devops-hb.oss-internal.cn-north-1.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.403.a81f9eb.20181127121007.bin -O installer && sh installer -- -a jcmagent /usr/local/share/jdcloud/ifrit && rm -f installer`  
华东-上海          | `wget -c http://devops-hd.oss-internal.cn-east-2.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.403.a81f9eb.20181127121007.bin -O installer && sh installer -- -a jcmagent /usr/local/share/jdcloud/ifrit && rm -f installer`  
华东-宿迁         | `wget -c http://devops-sq.oss-internal.cn-east-1.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.403.a81f9eb.20181127121007.bin -O installer && sh installer -- -a jcmagent /usr/local/share/jdcloud/ifrit && rm -f installer` 
华南-广州               | `wget -c http://devops.oss-internal.cn-south-1.jcloudcs.com/ifrit/ifrit-agent-external-v0.01.403.a81f9eb.20181127121007.bin -O installer && sh installer -- -a jcmagent /usr/local/share/jdcloud/ifrit && rm -f installer`  

![安装Agent](../../../../../image/Cloud-Detection/install-1.png)  

3. 敲击回车键，执行安装操作。  
![安装Agent](../../../../../image/Cloud-Detection/install-2.png)  
注：如果安装失败，1-3分钟后重新执行安装命令。多次失败，请联系客服。
