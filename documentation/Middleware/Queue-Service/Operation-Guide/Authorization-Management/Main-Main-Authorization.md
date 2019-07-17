# 跨主账号的授权

本章节为您介绍如何进行主账号对主账号的授权来实现控制队列服务的资源及安全管理。

#### 说明：

- 权限分割需要创建不同的IAM角色来实现

- 角色扮演者资源创建或者使用资源产生的费用统一划归到角色创建的主账号下

- 主账号拥有创建和删除角色及其策略的权限

  

#### 授权流程：

队列服务已全面对接访问控制 IAM服务，用户需要去[访问控制菜单](https://cm-console.jdcloud.com/cmSummary)进行设置进行主账号A对主账号B的授权。

1. 主账号A创建用户角色，例如RoleA并为用户角色授予相应的策略，[参考](https://docs.jdcloud.com/cn/iam/createrole)。

   - 系统策略可以参考：

     | 策略名称                          | 描述                 | 类型     |   资源范围                 | 备注                                                         |
     | --------------------------------- | -------------------- | -------- | -------------------------- | ------------------------------------------------------------ |
     | JDCloudQueueServiceAdmin          | 队列服务管理员权限   | 系统策略 | 主账号下队列服务的所有资源 | 队列的所有权限，包括管理及消息发送和接收                     |
     | JDCloudQueueServiceProduceMessage | 队列服务生产消息权限 | 系统策略 | 主账号下队列服务的所有资源 | 可以向已有queue发送消息                                      |
     | JDCloudQueueServiceConsumeMessage | 队列服务消费消息权限 | 系统策略 | 主账号下队列服务的所有资源 | 可以从已有queue接收消息以及进行修改消息的可见性超时时间和清空队列的操作 |
     | JDCloudQueueServiceManageQueue    | 队列服务队列管理权限 | 系统策略 | 主账号下队列服务的所有资源 | 可以创建、修改或者删除队列并且获得队列列表及详情信息         |
     | JDCloudResourceTagAdmin           | 标签服务管理员权限   | 系统策略 | 主账号下的所有资源         | 可以编辑资源标签，进行标签级别的资源筛选，如果想使用标签功能需要授予 |
     | JDCloudResourceTagRead            | 标签服务读权限       | 系统策略 | 主账号下的所有资源         | 可以查看标签，进行标签级别的资源筛选，建议授予此读权限       |

   - 自定义策略，[参考](https://docs.jdcloud.com/cn/iam/createpolicy)。（[策略语法可参考](https://docs.jdcloud.com/cn/iam/policy-management)，**资源ID填写队列名称**）

2. 登陆主账号B创建一个IAM子用户SubB，并授予**JDCloudStsAdmin**安全令牌系统策略，[参考](https://docs.jdcloud.com/cn/iam/createsubuser)。

3. 登陆IAM子用户SubB，进入子用户控制台，点击右上角菜单中的 “切换角色”，进行角色身份的登录，输入主账号A的accountID和RoleA的角色名称，登录后，SubB将以RoleA的身份和权限对主账号A的资源进行访问和管理。
