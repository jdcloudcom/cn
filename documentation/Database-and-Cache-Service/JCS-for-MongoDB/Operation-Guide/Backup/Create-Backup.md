# 手动创建备份

每个 MongoDB 实例最多可手动创建3个备份，备份文件长期保存在京东云对象存储，目前不收取任何费用。

## 注意事项

- 如当前已有3个手动备份，再次手动创建备份时会自动删除最早的一个手动备份。
- 如当前有进行中的备份任务，则此时不能再次发起创建备份任务。

## 操作步骤

1. 登录 [MongoDB 控制台](https://mongodb-console.jdcloud.com/mongodb)。
1. 在“实例列表”页面，选择目标实例，点击 **实例名称**，进入“实例详情”页面。
1. 在“实例详情”页面，依次点击 **备份与恢复**  >  **备份数据** ，进入“备份数据”页面。

   ![](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-019.png)

1. 在“备份数据”页面，点击 **创建备份**，打开“创建备份确认弹窗”。
1. 点击 **确定**，确认执行创建备份。
1. 您可以在“备份列表”中查看备份状态，如果备份状态变更为“已完成”，表示备份创建成功。

## 相关参考

- [下载备份文件](Download-Bckup.md)
- [根据备份创建实例](Create-Instance-by-Backup.md)
- [根据时间点创建实例](Create-Instance-by-Point-in-Time.md)
- [设置自动备份](Modify-Backup-Policy.md)
- [数据恢复](Restore-Instance.md)
