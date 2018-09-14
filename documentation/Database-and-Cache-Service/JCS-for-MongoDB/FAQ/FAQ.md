# 常见问题

**Q：云数据库 MongoDB 支持公网连接吗？**

A：出于安全考虑，云数据库 MongoDB 目前仅提供内网连接，暂不提供公网连接。如果您需要本地直接连接 MongoDB 实例，可以通过代理转发的方式实现，操作方式请参见“[公网连接 MongoDB 实例](../Best-Practices/Public-Network-Connect-to-MongoDB-Instance.md)”。


**Q：云数据库 MongoDB 哪些版本？**

A：云数据库 MongoDB目前支持3.2版，即将推出3.4版和3.6版。


**Q：云数据库 MongoDB 支持哪些协议？**

A：京东云云数据库MongoDB完全兼容MongoDB官方协议，使用方法可参见“[MongoDB官方文档](https://docs.mongodb.com/v3.2/introduction/)”。

**Q：oplog大小是多少，是否支持调整？**

A：oplog是实例存储空间的5%，暂不支持调整大小。

   
**Q：为什么看到监控里，MongoDB内存占用比很高？**

A：MongoDB使用的是内存映射存储引擎，它会把磁盘IO操作转换成内存操作，如果是读操作，内存中的数据起到缓存的作用，如果是写操作，内存还可以把随机的写操作转换成顺序的写操作，可以大幅度提升性能，用户不用担心内存占用比例较高的问题。如果内存容量已成为性能瓶颈请升级实例配置，操作方式请参见“[变更实例配置](../Operation-Guide/Instance-Management/Modify-Instance-Spec.md)”。
