# 删除和管理topic

## 注意事项
- 对于topic的拥有着，具有topic的管理权限和删除权限
- 对于被授权的topic，被授权使用者只有删除的权限，但不是真正删除topic，只是删除了授权

## 操作步骤
### 1.Topic管理页面的topic列表，选择想要删除topic所在行的“更多”按钮，选取“删除”
![删除和管理步骤1](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/删除暂停-01.png)
弹出提示框，点击“删除”，则topic被删除且删除后，将不再推送消息，并立即停止服务，数据无法恢复。  
### 2.Topic管理页面的topic列表，选择想要操作topic所在行的“更多”按钮，可选取“发送暂停”、“接收暂停”和“全部暂停”
![删除和管理步骤2](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/删除暂停-02.png)
弹出提示框，确认所需要的操作。
### 3.在订阅管理页面，可以重置消费位点
![删除和管理步骤3](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/删除暂停-03.png)
选取想要重置消费位点订阅关系中的“重置消费位点”按钮
![删除和管理步骤4](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/Message-Queue/删除暂停-04.png)

- 可以选择“清除所有累积消息”，所有未被消费的堆积消息将会被跳过，从最新的下一条消息开始消费。
- 可以选择“按时间进行消费位点重置”，选择在消息生命周期内的任意一个时间点来进行消费位点的重置，改变消费进度。
