# 限制说明
## 功能限制
### 数据源管理
当前仅支持单个数据源，如果需要同步两个数据源，需要购买两个实例。

### 实例恢复
针对已经删除的实例，不支持恢复。

### 创建实例
针对单地域的实例数是有限制的，一个地域默认最多支持 5 个实例，如果有更多实例需求，请提交工单。

### 数据库账号保留关键字
```
root, admin, eagleye, master, aurora, sa, sysadmin, administrator, mssqld, public, securityadmin, serveradmin, setupadmin, processadmin, diskadmin, dbcreator, bulkadmin, tempdb, msdb, model, distribution, mssqlsystemresource, guest, add, except, percent, all, exec, plan, alter, execute, precision, and, exists, primary, any, exit, print, as, fetch, proc, asc, file, procedure, authorization, fillfactor, public, backup, for, raiserror, begin, foreign, read, between, freetext, readtext, break, freetexttable, reconfigure, browse, from, references, bulk, full, replication, by, function, restore, cascade, goto, restrict, case, grant, return, check, group, revoke, checkpoint, having, right, close, holdlock, rollback, clustered, identity, rowcount, coalesce, identity_insert, rowguidcol, collate, identitycol, rule, column, if, save, commit, in, schema, compute, index, select, constraint, inner, session_user, contains, insert, set, containstable, intersect, setuser, continue, into, shutdown, convert, is, some, create, join, statistics, cross, key, system_user, current, kill, table, current_date, left, textsize, current_time, like, then, current_timestamp, lineno, to, current_user, load, top, cursor, national, tran, database, nocheck, transaction, dbcc, nonclustered, trigger, deallocate, not, truncate, declare, null, tsequal, default, nullif, union, delete, of, unique, deny, off, update, desc, offsets, updatetext, disk, on, use, distinct, open, user, distributed, opendatasource, values, double, openquery, varying, drop, openrowset, view, dummy, openxml, waitfor, dump, option, when, else, or, where, end, order, while, errlvl, outer, with, escape, over, writetext
```
