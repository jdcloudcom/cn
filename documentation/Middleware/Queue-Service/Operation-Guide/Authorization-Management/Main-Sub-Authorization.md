# 主账号对IAM子用户的授权

本章节为您介绍如何进行主账号对IAM子用户的授权来实现队列服务的资源控制和安全管理。

#### 说明：

- 权限分割需要创建不同的IAM子用户来实现

- IAM子用户创建或者使用资源产生的费用统一划归到主账号下

- 主账号拥有创建和删除IAM子用户及其策略的权限

  

#### 授权流程：

队列服务已全面对接访问控制 IAM服务，用户需要去[访问控制菜单](https://cm-console.jdcloud.com/cmSummary)设置IAM 子用户的权限。

1. 登陆控制台创建IAM子用户，[参考](https://docs.jdcloud.com/cn/iam/createsubuser)。

2. 为IAM子用户授权系统策略，[参考](https://docs.jdcloud.com/cn/iam/createsubuser)。

   系统预置授权策略：

   现在系统已经预置4种策略，用户可以按需授权给IAM子用户。

   | 策略名称                          | 描述                 | 类型     |   资源范围                | 备注                                                         |
   | --------------------------------- | -------------------- | -------- | -------------------------- | ------------------------------------------------------------ |
   | JDCloudQueueServiceAdmin          | 队列服务管理员权限   | 系统策略 | 主账号下队列服务的所有资源 | 队列的所有权限，包括管理及消息发送和接收                     |
   | JDCloudQueueServiceProduceMessage | 队列服务生产消息权限 | 系统策略 | 主账号下队列服务的所有资源 | 可以向已有queue发送消息                                      |
   | JDCloudQueueServiceConsumeMessage | 队列服务消费消息权限 | 系统策略 | 主账号下队列服务的所有资源 | 可以从已有queue接收消息以及进行修改消息的可见性超时时间和清空队列的操作 |
   | JDCloudQueueServiceManageQueue    | 队列服务队列管理权限 | 系统策略 | 主账号下队列服务的所有资源 | 可以创建、修改或者删除队列并且获得队列列表及详情信息         |
    | JDCloudResourceTagAdmin           | 标签服务管理员权限   | 系统策略 | 主账号下的所有资源         | 可以编辑资源标签，进行标签级别的资源筛选，如果想使用标签功能需要授予 |
    | JDCloudResourceTagRead            | 标签服务读权限       | 系统策略 | 主账号下的所有资源         | 可以查看标签，进行标签级别的资源筛选，建议授予此读权限       |

3. 或者创建自定义策略再进行授权，[参考](https://docs.jdcloud.com/cn/iam/createpolicy)。（[策略语法可参考](https://docs.jdcloud.com/cn/iam/policy-management)，**资源ID填写队列名称**）

4. 以IAM子用户登录名和密码登陆界面，进行符合权限的资源操作。

