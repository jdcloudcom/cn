# 大数据量处理
## 导入数据
如果有 Unique Key 并且业务端可以保证数据中没有冲突，可以在 Session 内打开这个开关：
```
SET @@session.tidb_skip_constraint_check=1;
```

另外为了提高写入性能，可以对 TiKV 的参数进行调优。
请特别注意这个参数：

```[raftstore]
# 默认为 true，表示强制将数据刷到磁盘上。如果是非金融安全级别的业务场景，建议设置成 false，
# 以便获得更高的性能。
sync-log = true
```

## 写入数据
上面提到了 TiDB 对单个事务的大小有限制，这层限制是在 KV 层面，反映在 SQL 层面的话，简单来说一行数据会映射为一个 KV entry，每多一个索引，也会增加一个 KV entry，所以这个限制反映在 SQL 层面是：

- 单行数据不大于 6MB
- 总的行数*(1 + 索引个数) < 30w
- 一次提交的全部数据小于 100MB

另外注意，无论是大小限制还是行数限制，还要考虑 TiDB 做编码以及事务额外 Key 的开销，在使用的时候，建议每个事务的行数不要超过 1w 行，否则有可能会超过限制，或者是性能不佳。

建议无论是 Insert，Update 还是 Delete 语句，都通过分 Batch 或者是加 Limit 的方式限制。

在删除大量数据的时候，建议使用 Delete * from t where xx limit 5000; 这样的方案，通过循环来删除，用 Affected Rows == 0 作为循环结束条件，这样避免遇到事务大小的限制。

如果一次删除的数据量非常大，这种循环的方式会越来越慢，因为每次删除都是从前向后遍历，前面的删除之后，短时间内会残留不少删除标记(后续会被 gc 掉)，影响后面的 Delete 语句。如果有可能，建议把 Where 条件细化。举个例子，假设要删除 2017-05-26 当天的所有数据，那么可以这样做：
```
for i from 0 to 23:
    while affected_rows > 0:
	delete * from t where insert_time >= i:00:00 and insert_time < (i+1):00:00 limit 5000;
	affected_rows = select affected_rows()
```

上面是一段伪代码，意思就是要把大块的数据拆成小块删除，以避免删除过程中前面的 Delete 语句影响后面的 Delete 语句。
