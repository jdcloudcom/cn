# 限制说明
TiDB 目前还不支持触发器、存储过程、自定义函数、外键，除此之外，TiDB 支持绝大部分 MySQL 5.7 的语法。

## 不支持的特性
- 存储过程
- 视图
- 触发器
- 自定义函数
- 外键约束
- 全文索引
- 空间索引
- 非 UTF8 字符集

## 与 MySQL 有差异的特性
**自增 ID**
TiDB 的自增 ID (Auto Increment ID) 只保证自增且唯一，并不保证连续分配。TiDB 目前采用批量分配的方式，所以如果在多台 TiDB 上同时插入数据，分配的自增 ID 会不连续。

**内建函数**
TiDB 支持常用的 MySQL 内建函数，但是不是所有的函数都已经支持，具体请参考[官方语法文档](https://pingcap.github.io/sqlgram/#FunctionCallKeyword)。

**DDL**
TiDB 实现了 F1 的异步 Schema 变更算法，DDL 执行过程中不会阻塞线上的 DML 操作。目前已经支持的 DDL 包括：
- Create Database
- Drop Database
- Create Table
- Drop Table
- Add Index
- Drop Index
- Add Column
- Drop Column
- Alter Column
- Change Column
- Modify Column
- Truncate Table
- Rename Table
- Create Table Like

## 事务
TiDB 使用乐观事务模型，在执行 Update、Insert、Delete 等语句时，只有在提交过程中才会检查写写冲突，而不是像 MySQL 一样使用行锁来避免写写冲突。所以业务端在执行 SQL 语句后，需要注意检查 commit 的返回值，即使执行时没有出错，commit的时候也可能会出错。

## Load data
TiDB 在执行 load data 时，默认每 2 万行记录作为一个事务进行持久化存储。如果一次 load data 操作插入的数据超过 2 万行，那么会分为多个事务进行提交。如果某个事务出错，这个事务会提交失败，但它前面的事务仍然会提交成功，在这种情况下一次 load data 操作会有部分数据插入成功，部分数据插入失败。而 MySQL 中会将一次 load data 操作视为一个事务，如果其中发生失败情况，将会导致整个 load data 操作失败。