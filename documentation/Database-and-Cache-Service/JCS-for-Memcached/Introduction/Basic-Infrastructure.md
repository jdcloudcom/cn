# 基础架构

   ![](https://github.com/jdcloudcom/cn/blob/JCS-for-Memcached/image/Memcached/1.png)
- 控制服务：主要用于处理来自用户和后端的请求任务如：创建、删除、查询、配置变更、failover、扩容缩容、配置修改、免密切换等任务。

- 监控服务：收集Memcached实例信息（资源使用、数据库键统计、命令使用、连接认证等信息）和宿主机信息（资源使用和网络流量等信息），并为用户提供前端控制台显示。

- 哨兵：哨兵监控Memcached实例是否存活，当发现实例down掉后，发送failover任务，自动创建新实例。

- 日志收集：收集Memcached实例运行及其他服务模块的日志信息。
