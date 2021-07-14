# 攻击告警设置

您可以在消息中心对告警消息的接收进行设置，确定需要接收消息告警的人和接收方式。

## 注意事项
- 告警设置对全局生效，包括 **DDoS基础防护** 、 **DDoS防护包** 和 **DDoS IP高防** 。

## 配置告警通知方式
告警的账号联系人和通知方式，请在 **消息中心** 进行配置。
1. 如果已登录控制台，请在控制台右上方，找到消息图标，进入消息管理-->消息设置页。
![消息中心](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/message%2004.png)
或直接登录[消息中心](https://message-console.jdcloud.com/message/message-list)。
2. 点击编辑图标，可设置告警通知联系人，可勾选邮件或手机短信通知。
![消息中心](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/message%2005.png)

##  配置告警通知类型

DDoS IP高防支持对单个实例进行DDoS攻击告警、状态码告警、黑洞告警三种类型进行配置。请在实例详情下，如图所示位置点击展开图标，展开告警设置进行配置：

![告警通知](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/alarm1.png)

告警类型如下：

- DDoS攻击告警通知：即攻击产生的告警、攻击结束的告警、未备案告警、带宽受限告警等信息的推送。
- 状态告警：即针对已添加的域名，当常见的异常状态码到达设置阈值时触发的告警通知。如500/502/504等。
- 黑洞告警通知：即黑洞开始和解封的告警通知。

##  状态码告警设置

1.开启开关，点击编辑图标，进入状态码告警设置页面。

![告警通知](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/alarm2.png)

2.选择域名，勾选状态码，设置阈值，点击确定。

![告警通知](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/alarm3.png)

状态码告警设置字段解释如下：

- 告警域名：选择需要告警的域名，支持选择全部域名。
- 状态码类型：500/502/504 为源站返回状态码，590/592/594 为高防节点返回状态码。
- 告警规则：状态码在5分钟内周期占比达到占比阈值时，或者5分钟内累计次数达到阈值时，则会触发告警，同一域名一天内最多6次告警。占比阈值可选5%/10%/30%/50%，次数阈值可设置1-1000000的整数。两个阈值条件满足其中任意一个即可触发告警。

## 查看告警通知
1. 登录 [消息中心](https://message-console.jdcloud.com/message/message-list)。
2. 在我的消息–>安全消息中，可以查看所有高防的安全消息告警。
![消息中心](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/message%2006.png)
