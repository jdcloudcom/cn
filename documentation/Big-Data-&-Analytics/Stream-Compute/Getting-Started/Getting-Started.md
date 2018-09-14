# 入门指南<br>
1. **准备工作**<br>
在使用流数据总线服务之前，首先需要注册京东云账号。<br><br>
2. **创建应用**<br>
第一步：登录流计算WEB控制台，进入流计算的“应用管理”页面，点击“创建”。<br>
![sc-002](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-002.png?raw=true)<br><br>
在创建应用界面中输入资料信息后点击确定, 应用创建完成.<br>
![sc-003](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-003.png?raw=true)<br>
应用名称: <br>
创建一个方便您记忆的应用名称<br><br>
任务类型: <br>
选择使用的底层计算引擎, 目前提供spark streaming-2.1.0, 后续将提供storm,和flink.<br><br>
流式计算单元: <br>
流式计算单元: 表示执行作业所消耗的计算资源, 一个流式计算单元包含1个CPU和4GB内存<br><br>
3. **作业开发**<br>
在应用列表页, 点击已创建的应用名称后, 进入到作业开发页面, 如下图:<br>
![sc-004](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-004.png?raw=true)<br><br>
一个完整的流式计算, 需要定义三部分内容, 如下图<br>
![sc-005](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-005.png?raw=true)<br><br>
4. **输入定义**<br>
首先需要定义流计算的输入源<br>
![sc-006](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-006.png?raw=true)<br><br>
5. **输出定义**<br>
计算完成后的数据需要输出到哪<br>
![sc-007](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-007.png?raw=true)<br><br>
6. **查询**<br>
查询即流计算作业开发, 首先需要创建一个进行作业开发的任务, 点击下图中的创建.<br>
![sc-008](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-008.png?raw=true)<br><br>
![sc-009](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-009.png?raw=true)<br><br>
创建完成后, 点击查询列表的作业名称, 进入开发页面<br>
![sc-010](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-010.png?raw=true)<br><br>
在开发页面中可以通过SQL的方式进行流式作业的开发.<br>
![sc-011](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-011.png?raw=true)<br>
语句说明:<br>
`insert into table order_partition select id,order_date from order_partitions`<br><br>
在SQL语句中 into table [tablename] 是您在 “输出” 界面定义的输出目标表。<br>
From [tablename] 是您在 “输入” 界面定义的输入来源.<br><br>
作业定义完成后, 在查询列表页,点击 “启动”运行作业任务.<br>
![sc-012](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-012.png?raw=true)<br>