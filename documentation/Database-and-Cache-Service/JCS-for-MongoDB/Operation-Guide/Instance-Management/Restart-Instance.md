# 重启实例

如果您的 MongoDB 实例运行异常，但不确认原因时，你可以考虑重启实例。

## 注意事项

- 重启实例会造成连接中断，请操作前请您务必确认已做好业务安排。
- 重启实例可能会导致主从切换，请务必确保应用使用Connection String URI的方式连接 MongoDB 实例。

## 前提条件

- 实例状态为运行，且计费状态正常。

## 操作步骤
1. 登录 [MongoDB 控制台](http://mongodb-console.jdcloud.com/mongodb)。
1. 在"实例列表"页面，选择目标实例，在操作项中，点击 **重启**，打开确认弹窗。

   ![重启实例](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-013.png)
   
1. 在确认弹窗中，点击 **确定**。
1. 实例状态变更为“重启中”，等待重启完成。
2. 重启完成后，实例状态将变更为“运行”。

    说明：实例重启服务会依次重启三个物理节点，通常在数分钟内完成。

## 相关参考

- [创建实例](../../Getting-Started/Create-Instance.md)
- [变更配置](Modify-Instance-Spec.md)
- [续费实例](Renewal-Instructions.md)


