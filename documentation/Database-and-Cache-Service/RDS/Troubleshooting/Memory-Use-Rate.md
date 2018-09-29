# 内存使用率
针对云数据库 MySQL/Percona，京东云提供了实例级的内存使用率监控和报警服务，具体的操作步骤请查看 [设置报警规则](../Operation-Guide/Monitor-Alarm/Set-Alarm-Rules.md)。

## 内存占用
云数据库 MySQL/Percona 的内存占用主要分为以下两项：
* 共享内存
* session 内存

## 共享内存
共享内存是云数据库 MySQL/Percona 实例创建的时候预先分配的内存空间；在共享内存中，innodb_buffer_pool 所占用的空间是最大的，它的大小由云数据库 Percona 的参数 innodb_buffer_pool_size 来指定。

innodb_buffer_pool 缓存的是云数据库 MySQL/Percona 实例的数据和索引信息。

## Session 内存
客户端和云数据库 MySQL/Percona 实例建立连接的时候，云数据库 MySQL/Percona 实例针对每一个连接会分配一个 session 内存。

session 内存的大小由以下云数据库 MySQL/Percona 的参数共同指定:
* sort_buffer_size
* read_buffer_size
* read_nd_buffer_size
* join_buffer_size
* thread_stack
* binlog_cache_size
* tmp_table_size

## 为什么内存使用率 100%
通过上面针对内存占用的分析，其实可以发现，云数据库 MySQL/Percona 实例访问越频繁，连接越多，其内存使用率很有可能会达到 100%，在大部分情况下这个是属于正常现象，表明你的云数据库 MySQL/Percona 正在满负荷工作。

## 降低内存使用率
当然，如果没有正确使用云数据库 MySQL/Percona 也会导致实例的内存使用率达到 100%，可以通过以下步骤去确认具体是什么原因导致的：
1. 如果在没用使用连接池的情况下，确保应用程序使用完数据库访问后，释放了连接，否则无用连接累计会导致内存使用率升高。
2. 确认 session 内存的相关云数据库 MySQL/Percona 的参数设置是否合理（建议采用云数据库 MySQL/Percona 实例默认设置的值，不对其做修改）。
3. 确认活跃连接数是否过多（建议活跃连接数不超过云数据库 MySQL/Percona 实例的 cpu 核数）。
4. 优化 SQL 语句（尽量避免使用临时表，可能会导致内存使用率迅速飙升；join，union，distinct 等其他命令都会导致临时表产生）。
5. 确保进行 SQL 查询的数据结果都是你需要的内容，不返回无用数据，导致占用额外的实例内存。
