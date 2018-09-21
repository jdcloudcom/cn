## 数据输入<br>
在应用列表页, 点击已创建的应用名称后, 进入到作业开发页面, 如下图:<br>
![sc-015](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-015.png?raw=true)<br><br>
一个完整的流式计算, 需要定义三部分内容, 首先需要先定义数据的 “输入”, 即流计算中的数据从哪来.<br>
![sc-016](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-016.png?raw=true)<br><br>
点击 “创建”后进入输入源定义页面.<br>
![sc-017](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-017.png?raw=true)<br><br>
名称: <br>
输入源的名称, 在后面查询作业的SQL语句中, from [tablename] 的tablename是此处您定义的名称.<br><br>
源类型: <br>
您可以选择来源于 “流数据总线” 中的数据, 在后续的版本迭代中将会提供更加丰富的源类型<br><br>
主题: <br>
您在 “流数据总线”中所创建的主题名称.<br><br>
Batch Interval：<br>
Batch Interval是将流式实时数据按照您此处设置的时间生成 mirco-batch （秒）<br><br>
消息格式: <br>
定义消息格式 JSON 或者 CSV<br><br>
分隔符: <br>
定义流数据总线中消息的分隔符, 以供进行数据解析,进行结构化处理<br><br>
![sc-018](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-018.png?raw=true)<br><br>
Schema: <br>
定义好分隔符后, 在此处定义解析的schema信息, 数据进行结构化处理后方可在流计算中进行处理分析<br>
![sc-019](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-019.png?raw=true)