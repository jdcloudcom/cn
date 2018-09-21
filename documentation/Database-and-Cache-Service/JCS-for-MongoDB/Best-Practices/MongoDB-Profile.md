# MongoDB 开启慢日志分析


使用 MongoDB 的 profile 命令可以启用、禁用或更改查询分析级别，以获取数据库性能相关的数据。默认情况下分析器处于关闭状态，您可根据业务情况自行设定。

## 注意事项

- 数据库分析系统会将查询内容写入日志，对性能有一定影响。


## 操作步骤

1. 查询分析器状态。

   > db.getProfilingStatus()
   
1. 修改分析器级别。

   > db.setProfilingLevel(level, slowms)

   - evel：0，关闭；1，记录慢速操作；2，记录所有操作。
   - slowms：时间阈值，单位ms。
	
1. 查询记录信息。
	
   Mongo Profile 记录存储在amdin库中，集合名为system.profile ，只要查询这个Collection的记录就可以获取到Profile信息。

   > use admin   #在admin库执行
   
   > db.system.profile.find()
   
   
## Profile记录说明

参数 | 说明
---|---
ts	| 该命令在何时执行。
millis Time	| 该命令执行耗时，以毫秒记。
info	| 本命令的详细信息。
query	| 表明这是一个query查询操作。
ntoreturn	| 本次查询客户端要求返回的记录数.比如, findOne()命令执行时 ntoreturn 为 1.有limit(n) 条件时ntoreturn为n。
query	| 具体的查询条件(如x>3)。
nscanned	| 本次查询扫描的记录数。
reslen	| 返回结果集的大小。
nreturned	| 本次查询实际返回的结果集。
update	| 表明这是一个update更新操作。
fastmod	| 表示一个快速修改操作，这些操作通常是相当快的。
fastmodinsert 	| 表示执行upsert的快速修改操作。
upsert	| 表明update的upsert参数为true.此参数的功能是如果update的记录不存在，则用update的条件insert一条记录。
moved |	表明本次update是否移动了硬盘上的数据，如果新记录比原记录短，通常不会移动当前记录，如果新记录比原记录长，那么可能会移动记录到其它位置，这时候会导致相关索引的更新.磁盘操作更多，加上索引更新，会使得这样的操作比较慢。
insert |	这是一个insert插入操作。
getmore	| 这是一个getmore 操作，getmore通常发生在结果集比较大的查询时，第一个query返回了部分结果，后续的结果是通过getmore来获取的。
