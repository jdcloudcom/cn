# 创建资源
在消息队列 JCQ中，消息的生产和消费需要通过主题订阅的形式，故用户首先要创建消息主题（topic），发送消息到某个指定的消息主题，而消费者通过订阅该消费主题进行消息消费。

## 前提条件
- 已注册京东云账号，并完成实名认证，且保证账户处于正常状态，没有在黑名单中。如果还没有账号请 [注册](https://accounts.jdcloud.com/p/regPage?source=jdcloud%26ReturnUrl=%2f%2fuc.jdcloud.com%2fpassport%2fcomplete%3freturnUrl%3dhttp%3A%2F%2Fuc.jdcloud.com%2Fredirect%2FloginRouter%3FreturnUrl%3Dhttps%253A%252F%252Fwww.jdcloud.com%252Fhelp%252Fdetail%252F734%252FisCatalog%252F1)，并 [实名认证](https://uc.jdcloud.com/account/certify)。
- 因为产品的计费类型为按用量计费，请确认您的账户不能处于欠费状态。

## 注意事项
- 公测期间用户最多只能创建5个topics。
- 对于某个topic的订阅Consumer Group数量没有限制。

## 步骤一：创建消费主题

1. 进入京东云控制台，菜单互联网中间件-消息队列 JCQ-Topic管理。
2. 首先选择想要创建资源的区域（比如华北），然后点击“新建”按钮，创建topic。
3. 创建topic中需要填写“topic名称”、选择消息类型和填写备注。

### 说明：

1. topic名称为全局唯一，如果有相同名称的topic被创建，则无法创建成功。并且topic只能包含字母、数字、连字符(-)、下划线(_)、波形符 (~)或加号 (+)，长度 为3-64 个字符。
2. 消息类型非为无序消息和全局顺序消息。

- 无序消息：不保证先入先出（FIFO）的顺序消费，包含普通消息和延时消息。
- 全局顺序消息：消息的生产和消费按照消息的发布顺序进行（FIFO）。

## 步骤二：添加订阅

1. 在Topic管理页面中，找到想要订阅的topic，在操作中可以选择订阅。
2. 在添加订阅者中需要新建/绑定已有Consumer Group ID，选择传送类型。

### 说明：

1. Consumer Group ID为全局唯一，如果有相同名称的Consumer Group ID被创建，则无法创建成功。并且Consumer Group ID只能包含字母、数字、连字符(-)和下划线(_)，长度7-64字符。
2. Consumer Group ID 和topic的关系是多对多关系（N：M），同一个Consumer Group ID可以订阅多个topic，同一个topic可以对应多个Consumer Group ID。
3. 选择发送消息的类型，包括SDK和 Http两种方式。
4. 订阅者tag的规则说明：tag是消息订阅者对于消息的筛选，当订阅者设置了tag时，有相同tag的消息才能被订阅者消费，如果没有设置tag，则订阅者对消息不做筛选。单个订阅者可最多可添加5个标签，单个标签为不超过64个字符的字符串，以‘,’号分割。
- 对于消息1，没有消息tag，订阅者有tag，则该订阅者不匹配，收不消息；
- 对于消息2， 消息有tag， 订阅者没有tag，投递时消息不用匹配，订阅者都能收到消息；
- 对于消息3，消息有tag，订阅者也有tag的时候，两者匹配的，才能收到消息；
- 对于消息4，消息没有tag，订阅者也没有tag，投递后，所有订阅者都能收到消息。

## 步骤三：创建 AccessKey和 SecretKey
在调用消息队列 JCQ的SDK或者openAPI进行消息的发送消费和管理操作时候，还需要验证用户的身份信息，即需要在控制台创建AccessKey和 SecretKey。
### 创建方法：
在京东云用户中心账户管理下的[AccessKey管理页面](https://uc.jdcloud.com/account/accesskey)申请AccessKey和SecretKey密钥对（简称AK/SK）。
AK/SK信息请妥善保管，如果遗失可能会造成非法用户使用此信息操作您在云上的资源，给你造成数据和财产损失。AK/SK密钥对允许启用、禁用，启用后可用其调用OpenAPI，禁用后不能用其调用OpenAPI。
