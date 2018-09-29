# 设置报警规则

在 Redis 控制台，您可以根据监控项设置报警规则，当监控项达到设置的阈值时，我们会通过短信和邮件的方式向您发送报警信息。

## 注意事项

- 缓存Redis实例创建成功后，会自动设置一条报警规则：“统计周期2分钟 磁盘使用率 平均值 >= 75 %, 持续5个周期”，您可以根据实际情况修改。


## 操作步骤

1. 登录 [Redis 控制台](https://Redis-console.jdcloud.com/Redis)。
1. 在"实例列表"页面，选择目标实例，点击 **实例名称**，进入"实例详情"页面。
1. 在"实例详情"页面，点击 **监控**，进入"监控信息"页面。
1. 点击页面右侧 **设置报警规则**，进入"报警规则"页面。

   ![](https://github.com/jdcloudcom/cn/blob/JCS-for-Redis/image/Redis/set-rule.png)
   
   
1. 在“报警规则”页面，点击 **新增报警规则**，进入”设置报警规则“页面，按页面提示添加新规则。
 
   ![](https://github.com/jdcloudcom/cn/blob/JCS-for-Redis/image/Redis/addrule.png)

## 相关参考

- [查看监控信息](Monitoring.md)
