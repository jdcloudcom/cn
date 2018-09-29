# 重发消息（死信队列）
在超过最大尝试推送次数后会将消息发送到死信队列。可将其作为无法成功处理 (使用) 的消息的目标的队列。  
可以在死信队列中留出和隔离这些消息以确定其处理失败的原因。区分消息类型(普通、顺序)。可按照Topic和ConsumerGroup ID进行搜索。

## 前提条件

- 消费失败的消息在消息生命周期内（3天）

## 注意事项

- 死信队列存储发送失败消息的上限为10000条
- 到达死信队列上限后，topic会暂停发送消息功能，待用户处理订阅者的异常

## 操作步骤
### 1. 进入死信队列页面

![死信队列1](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/死信队列-01.png)
输入topic ID 或者consumer group ID进行搜索

### 2. 重新发送和全部删除

![死信队列2](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/死信队列-02.png)  
对于死信可以选择全部重新发送或者全部删除  

- 全部重新发送，死信将再次进入topic发送给这条订阅关系的订阅者
- 全部删除，死信将全部删除，不再发送  

也可以点击“累计死信条数”，进入死信详情页面，进行单条死信的删除和重发
