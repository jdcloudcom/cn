# 一. 功能限制
为了保证实例的稳定和安全，SQL Server在功能上有部分限制，具体如下：

1.  不支通过命令行创建、删除数据库，不提供创建、删除和修改账号的操作。如果需要，可以通过控制台进行相关的操作。

2.  暂不提供以下功能：
- 集成服务（Integration Service）
- 报表服务（Reporting Service）
- 分析服务（Analysis Service）
- 服务代理（Servie Broker）
- 复制功能

# 二. 子账号限制

1. 云数据库SQL Server绝大部分功能支持主子账号，可以通过【管理】--> 【访问控制】对子账号的权限进行控制

2. 部分功能暂不支持子账号，具体如下：
- 不能创建SQL Server实例
- 不支持续费
- 不支持查看监控页面
- 不支持通过DMS登录数据库

# 三. 数量限制
每个地域下，每个账户能创建 **5个** SQL Server实例。 如果你需要创建更多的实例，请提交工单申请更多的配额。

# 四. 名称及密码限制

- **实例名：** 只支持中文、数字、小写字母及英文下划线“_”，且不少于2字符不超过32字符；
- **备份名称：** 只支持中文、数字、大小写字母及英文下划线“_”,不超过64字符
- **数据库名：** 只支持数字、小写字母及英文下划线“_”，必须以字母开头，字母或数字结尾，且不少于2字符不超过32个字符；
- **账号名：** 只支持数字、大小写字母及英文下划线“_”，必须以字母开头，字母或数字结尾，且不少于2字符不超过16个字符；
- **密码：** 不可为空，密码必须包含大小写字母及数字，长度8 - 32字符，特殊字符可选，支持-=;,./~!@#$%^&*()_+-|{}:<>? 即除`[]'"外的ASCII字符；

# 五. 保留关键字

数据库名和账号名不能使用以下关键字：<br>
root, admin, eagleye, master, aurora, sa, sysadmin, administrator, mssqld, public, securityadmin, serveradmin, setupadmin, processadmin, diskadmin, dbcreator, bulkadmin, tempdb, msdb, model, distribution, mssqlsystemresource, guest, add, except, percent, all, exec, plan, alter, execute, precision, and, exists, primary, any, exit, print, as, fetch, proc, asc, file, procedure, authorization, fillfactor, public, backup, for, raiserror, begin, foreign, read, between, freetext, readtext, break, freetexttable, reconfigure, browse, from, references, bulk, full, replication, by, function, restore, cascade, goto, restrict, case, grant, return, check, group, revoke, checkpoint, having, right, close, holdlock, rollback, clustered, identity, rowcount, coalesce, identity_insert, rowguidcol, collate, identitycol, rule, column, if, save, commit, in, schema, compute, index, select, constraint, inner, session_user, contains, insert, set, containstable, intersect, setuser, continue, into, shutdown, convert, is, some, create, join, statistics, cross, key, system_user, current, kill, table, current_date, left, textsize, current_time, like, then, current_timestamp, lineno, to, current_user, load, top, cursor, national, tran, database, nocheck, transaction, dbcc, nonclustered, trigger, deallocate, not, truncate, declare, null, tsequal, default, nullif, union, delete, of, unique, deny, off, update, desc, offsets, updatetext, disk, on, use, distinct, open, user, distributed, opendatasource, values, double, openquery, varying, drop, openrowset, view, dummy, openxml, waitfor, dump, option, when, else, or, where, end, order, while, errlvl, outer, with, escape, over, writetext
