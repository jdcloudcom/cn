# Agent升级操作说明
## 申请AK/SK  
1.以管理员身份登录管理控制台https://console.jdcloud.com，点击登录用户->Access Key管理。  

![](https://raw.githubusercontent.com/luolei-laurel/cn/patch-6/image/Cloud-Monitor/Usability-Monitor/aksk.png)  

2.若无Access Key，则点击“创建Access Key”，执行创建操作。若已有ak/sk,则直接粘贴备用（建议创建云监控agent专用的ak/sk）。  

## 配置credential文件  
1.登录可用性监控任务选择作为探测源的云主机。  
2.配置用户鉴权的credential文件
   - 创建~/.jdc/monitor_credentials.yml文件
   - 编缉并保存monitor_credentials.yml文件，文件内容为：
   ```
   ak: xxxxxxx(填写YourAccessKeyID)   
   sk: xxxxxxx(填写YourAccessKeySecret) 
   ```  
   注：ak\sk内容填写须符合yaml语法（键值对之间必须要有空格），否则会读取ak\sk失败。如: ak:(空格)xxxxxx
