## 数据输出<br>
输出定义: <br>
计算完成后的数据需要输出到哪<br><br>
![sc-020](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-020.png?raw=true)<br><br>
名称: <br>
输出源的名称, 在后面查询作业的SQL语句中, into [tablename] 的tablename是此处您定义的名称.<br><br>
输出位置: <br>
您可以选择计算后的数据输出到哪, 目前提供的输出位置是 “数据计算服务”和 “流数据总线”, 在后续的版本迭代中将会提供更加丰富的输出目标端<br><br>
A)	输出位置: 数据计算服务<br>
数据库: <br>
数据计算服务下的数据库名称:<br><br>
数据表: <br>
数据库下的数据表名称<br><br>
B) 输出位置: 流数据总线<br>
流数据总线主题:<br>
选择您在流数据总线下创建的主题名称<br><br>
事件序列化格式:<br>
选择事件序列化格式JSON或CSV<br><br>
异常数据处理: <br>
忽略异常数据, 不保存: 当遇到异常数据时, 异常数据将被忽略, 继续继<br>
![sc-021](https://github.com/jdcloudcom/cn/blob/edit/image/Streamcompute/SC-021.png?raw=true)<br>
续后面合规的数据<br>
忽略异常数据, 并保存: 当开启此选项后, 异常数据将保存到您指定的云存储bucket中, 如下图所示<br><br>
点击确定后, 输出定义完成. <br>
