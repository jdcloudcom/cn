# Binlog 文件上传
Binlog 文件记录实例的事务信息，是云数据库 MySQL/Percona/MariaDB 实例 HA 架构以及高可用性、可恢复性的基础。
云数据库 MySQL/Percona/MariaDB 实例会定期自动同步 Binlog 文件至云存储，并在48小时后清理本地 Binlog 文件，届时可以释放实例本地的存储空间供其他用途使用。
如果实例在短时间内产生大量 Binlog 文件，可用通过控制台提供的 ***一键上传 Binlog*** 功能，主动同步 Binlog 文件至云存储，并清理本地 Binlog 文件。

## 注意事项
* 目前京东云暂不收取 Binlog 所产生的空间占用费用。
* 您主动进行一键上传 Binlog 操作后，清理实例最后一个备份前的全部本地 Binlog 文件。

## 上传本地 Binlog 文件
1. 进入 [云数据库 RDS 控制台](https://rds-console.jdcloud.com/database)。
2. 选择需要进行 Binlog 清理的目标实例，点击目标实例的名称，进入到实例详情页。
3. 选择 ***备份管理*** 标签，点击 ***Binlog*** 标签进入 Binlog 的列表页，点击 ***一键上传Binlog*** 按钮，执行 Binlog 文件主动上传操作。
