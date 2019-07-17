# 日志转储

## 一、转储配置

### 1.创建转储任务

创建转储任务需要确认已添加采集配置，否则无法创建转储任务。

1）进入对应的日志集，在需要转储的日志主题后方的“管理”中点击“转储配置”，进入转储配置页面。

![](https://raw.githubusercontent.com/jdcloudcom/cn/zhangwenjie-only/image/LogService/LogTransfer/logtransfer1.png)

2）转储信息配置

![](https://raw.githubusercontent.com/jdcloudcom/cn/zhangwenjie-only/image/LogService/LogTransfer/logtransfer2.png)

点击“新建转储任务”，填写转储任务名称，不为空，且只允许中文，数字，大小写字母，英文下划线“_”及中划线“-”，不超过32字符。

选择需要转储的京东云对象存储，该对象存储需要和当前转储的日志集和日志主题处于同一地域，如果用户当前账号下该地域没有对象存储资源，可点击“新建对象存储”，快速创建对象存储资源。

输入目录前缀。前缀以非/开头，若不设置目录前缀，则默认为当前日志集名称/日志主题名称/，例如servicecode/test-log/test-logapi。

填写分区格式。根据strptime时间格式化自动生成目录，例如，填写分区格式为 %Y/%m/%d，生成的目录 2017/07/16。最终投递的文件目录为：{OSS存储桶}/{目录前缀}/{分区格式}_{转储任务id}_{转储任务批次}。

选择转储文件大小和转储时间间隔。

选择转储格式，以及是否压缩，如果需要压缩，则选择需要压缩的格式。

点击“保存”，完成转储任务的创建。

转储任务创建完成后延迟约15分钟后开始进行转储。


### 2.停止转储任务

进入转储配置页面，选择需要停止的转储任务，点击后方的停止转储，即可停止转储日志数据。

![](https://raw.githubusercontent.com/jdcloudcom/cn/zhangwenjie-only/image/LogService/LogTransfer/logtransfer3.png)

点击日志服务左侧菜单的“日志转储专利”，选择需要转储的日志集，日志主题，以及转储任务，点击“停止转储”，即可停止转储日志数据。

![](https://raw.githubusercontent.com/jdcloudcom/cn/zhangwenjie-only/image/LogService/LogTransfer/logtransfer4.png)

## 二、日志转储管理

点击转储配置中转储任务后面的“查看”或者点击日志服务左侧菜单中的“日志转储管理”，即可进入该页面。

日志转储管理中可以进行停止转储任务、修改转储配置的操作，同时可查看转储任务中的文件转储状态，如果有转储失败则可在一小时内进行重试操作，超过一小时后，不可重试。
