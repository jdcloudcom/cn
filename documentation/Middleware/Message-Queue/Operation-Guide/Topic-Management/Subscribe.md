# 订阅topic
## 前提条件
- 已经创建好topic

## 注意事项
- 对于某个topic的订阅Consumer Group数量没有限制。
- 可以选择已有的Consumer Group，也可选择新建Consumer Group。


## 操作步骤
### 1. 在topic列表，选择想要订阅topic所在行的“订阅”按钮

![订阅步骤1](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/订阅-01.png)

### 2.填写完订阅者信息，点击“订阅”按钮

![订阅步骤2](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/订阅-02.png)  
I. Consumer Group ID为全局唯一，如果有相同名称的Consumer Group ID被创建，则无法创建成功。并且Consumer Group ID只能包含字母、数字、连字符(-)和下划线(_)，长度7-64字符。  
II. Consumer Group ID 和topic的关系是多对多关系（N：M），同一个Consumer Group ID可以订阅多个topic，同一个topic可以对应多个Consumer Group ID。  
III. 选择发送消息的类型，包括SDK和 Http两种方式。  
IV. 订阅者tag的规则说明：tag是消息订阅者对于消息的筛选，当订阅者设置了tag时，有相同tag的消息才能被订阅者消费，如果没有设置tag，则订阅者对消息不做筛选。单个标签为不超过64个字符的字符串，以‘,’号分割。

- 对于消息1，没有消息tag，订阅者有tag，则该订阅者不匹配，收不消息；
- 对于消息2， 消息有tag， 订阅者没有tag，投递时消息不用匹配，订阅者都能收到消息；
- 对于消息3，消息有tag，订阅者也有tag的时候，两者匹配的，才能收到消息；
- 对于消息4，消息没有tag，订阅者也没有tag，投递后，所有订阅者都能收到消息。

### 3.可在topic详情-订阅管理，查询订阅信息

![订阅步骤3](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/订阅-03.png)
可以点击“取消订阅”，完成取消订阅的操作
