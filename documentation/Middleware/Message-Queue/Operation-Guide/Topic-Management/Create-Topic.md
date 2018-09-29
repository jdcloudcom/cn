# 创建Topic
  在Topic管理页面可以进行topic的创建
  
 ## 前提条件
 
- 已注册京东云账号，并完成实名认证，且保证账户处于正常状态，没有在黑名单中。如果还没有账号请 [注册](https://accounts.jdcloud.com/p/regPage?source=jdcloud%26ReturnUrl=%2f%2fuc.jdcloud.com%2fpassport%2fcomplete%3freturnUrl%3dhttp%3A%2F%2Fuc.jdcloud.com%2Fredirect%2FloginRouter%3FreturnUrl%3Dhttps%253A%252F%252Fwww.jdcloud.com%252Fhelp%252Fdetail%252F734%252FisCatalog%252F1)，并 [实名认证](https://uc.jdcloud.com/account/certify)。
- 因为产品的计费类型为按用量计费，请确认您的账户不能处于欠费状态。

## 注意事项
- 公测期间用户最多只能创建5个topics。


## 操作步骤
### 1.Topic管理页面点击“新建”按钮

从控制台左侧菜单中，找到互联网中间件-消息队列 JCQ-Topic管理页面，点击新建
 ![创建topic步骤1](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/创建topic-01.PNG)

### 2.填写完Topic信息，点击“创建”按钮

页面刷新，完成新topic的创建
 ![创建topic步骤2](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/创建topic-02.png)  
I. topic名称可以按照提示信息输入，不可修改。  
II. 消息类型分为无序消息和全局顺序消息:  

- 无序消息：不保证先入先出（FIFO）的顺序消费，包含普通消息和延时消息。
- 全局顺序消息：消息的生产和消费按照消息的发布顺序进行（FIFO）。  

III. 备注根据需求填写，不可超过255个字节。
