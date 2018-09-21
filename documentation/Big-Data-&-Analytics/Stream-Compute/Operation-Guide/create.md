# 操作指南<br>
## 创建应用<br>
1. **准备工作**<br>
在使用流数据总线服务之前，首先需要注册京东云账号。<br><br>
2.	**创建应用**<br>
第一步：登录流计算WEB控制台，进入流计算的“应用管理”页面，点击“创建”。<br>
![sc-013](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-013.png?raw=true)<br><br>
在创建应用界面中输入资料信息后点击确定, 应用创建完成.<br>
![sc-014](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-014.png?raw=true)<br>
应用名称: <br>
创建一个方便您记忆的应用名称<br><br>
任务类型: <br>
选择使用的底层计算引擎, 目前提供spark streaming-2.1.0, 后续将提供storm,和flink.<br><br>
流式计算单元: <br>
流式计算单元: 表示执行作业所消耗的计算资源, 一个流式计算单元包含1个CPU和4GB内存<br><br>
注意此处的流式计算单元是您后面可使用的计算单元最高上限.<br>
例如, 您在创建应用时选择了20个流式计算单元, 进入应用后创建了4个作业任务, 针对每个作业任务, 您可以独立的分配计算资源, 但是分配给4个作业任务的计算资源总和不能超过此处定义的流式计算单元