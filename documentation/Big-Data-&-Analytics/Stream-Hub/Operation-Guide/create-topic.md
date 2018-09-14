# 入门指南<br>
## 创建主题<br>
1. 准备工作<br>
在使用流数据总线服务之前，首先需要注册京东云账号。<br><br>
2. 创建主题<br>
第一步：登录WEB控制台，进入流数据总线的“主题管理”页面，点击“新建主题”。<br>
![创建主题](https://github.com/jdcloudcom/cn/blob/edit/image/DataBus/db-004.png?raw=true)<br><br>
第二步：填写主题基本信息，点击“确认”，主题创建完成。<br>
![填写信息](https://github.com/jdcloudcom/cn/blob/edit/image/DataBus/db-005.png?raw=true)<br><br>
Shard: 数据的处理能力, 1个shard对应1MB/s 或 1000条数据写入, 2MB/s数据读取<br><br>
Partition数量: 创建所需要的partition分区数量 1-20, 主题创建后分区数量不允许再次修改.<br><br>
生命周期: 数据可以在流数据总线中存储 1 – 7 天<br>
