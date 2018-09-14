## 数据归档<br>
接入到流总线的数据最长可以保存7天, 如果您需要将数据永久保存下来, 需要开启归档功能, 并把数据持久化到您想保存的地方<br><br>
1. 点击所创建的主题名称<br>
![选择主题](https://github.com/jdcloudcom/cn/blob/edit/image/DataBus/db-006.png?raw=true)<br><br>
2. 进入该主题的详细页面后, 点击左侧的 “归档”, 并开启右侧的开启按钮<br>
![开启归档](https://github.com/jdcloudcom/cn/blob/edit/image/DataBus/db-007.png?raw=true)<br><br>
3. 配置归档信息<br>
![归档配置](https://github.com/jdcloudcom/cn/blob/edit/image/DataBus/db-008.png?raw=true)<br><br>
归档除法条件:数据进行归档的触发条件,可以已时间或者数据量大小为条件进行归档的触发条件<br><br>
归档目标设置: 可以选择数据归档到的目的地. 例如数据计算服务, 云存储. <br><br>
如果选择了数据计算服务, 后面需要选择 “数据库” “数据表”.<br><br>
消息识别模式: <br>
    - 分隔符识别schema: 您可以自己制定数据的分隔符,以便程序对消息进行解析处理<br>
    - JSON识别schema: 系统将自动识别json文件,并进行解析<br><br>
消息样式:<br>
![消息样式](https://github.com/jdcloudcom/cn/blob/edit/image/DataBus/db-009.png?raw=true)<br><br>
 输入消息样例后, 系统将根据您输入的分隔符识别schema, 在字段对照中, 您需要对解析后的归档字段和目标端库表中的字段进行对应关系映射.<br><br>
配置好映射关系后,点击确认完成归档设置

