# 限制说明
## 最大连接数限制
### MySQL
|实例规格|最大连接数|
|---|---|
|1核 1GB|300|
|1核 2GB|600|
|1核 4GB|1200|
|2核 8GB|2000|
|4核 16GB|4000|
|8核 32GB|8000|
|16核 64GB|16000|

### MySQL 只读实例
|实例规格|最大连接数|
|---|---|
|1核 1GB|300|
|1核 2GB|600|
|1核 4GB|1200|
|2核 8GB|2000|
|4核 16GB|4000|
|8核 32GB|8000|
|16核 64GB|16000|

## 功能限制
### 缩容操作
* 现在不支持实例的缩容。

### 数据库版本升级
* 现在不支持数据库版本的升级。例如 MySQL 5.6 升级到 MySQL 5.7。

### 实例恢复
* 针对已经删除的实例，不支持恢复。

### 创建实例
* 针对单地域的实例数是有限制的，一个地域默认最多支持 5 个实例，如果有更多实例需求，请提交工单。

### 数据库库名保留关键字
```
mysql，information_schema，performance_schema，sys，percona, admin, aurora, replicator, xtrabak, root, mysql, test, eagleye, information_schema, guest, add, analyze, asc, between, blob, call, change, check, condition, continue, cross, current_timestamp, database, day_microsecond, dec, default, desc, distinct, double, each, enclosed, exit, fetch, float8, foreign, goto, having, hour_minute, ignore, infile, insensitiv, int1, int4, interval, iterate, keys, leading, like, lines, localtimestamp, longblob, low_priority, mediumint, minute_microsecond, modifies, no_write_to_binlog, on, optionally, out, precision, purge, read, references, rename, require, revoke, schema, select, set, spatial, sqlexception, sql_big_result, ssl, table, tinyblob, to, true, unique, update, using, utc_timestamp, varchar, when, with, xor, all, and, asensitive, bigint, both, cascade, char, collate, connection, convert, current_date, current_user, databases, day_minute, decimal, delayed, describe, distinctrow, drop, else, escaped, explain, float, for, from, grant, high_priority, hour_second, in, inner, insert, int2, int8, into, join, kill, leave, limit, load, lock, longtext, match, mediumtext, minute_second, natural, null, optimize, or, outer, primary, raid0, reads, regexp, repeat, restrict, right, schemas, sensitive, show, specific, sqlstate, sql_calc_found_rows, starting, terminated, tinyint, trailing, undo, unlock, usage, utc_date, values, varcharacter, where, write, year_month, alter, as, before, binary, by, case, character, column, constraint, create, current_time, cursor, day_hour, day_second, declare, delete, deterministic, div, dual, elseif, exists, false, float4, force, fulltext, group, hour_microsecond, if, index, inout, int, int3, integer, is, key, label, left, linear, localtime, long, loop, mediumblob, middleint, mod, not, numeric, option, order, outfile, procedure, range, real, release, replace, return, rlike, second_microsecond, separator, smallint, sql, sqlwarning, sql_small_result, straight_join, then, tinytext, trigger, union, unsigned, use, utc_time, varbinary, varying, while, x509, zerofill, jcloud_yunding_db_push, jcloudv_push_rw, jcloudv_push_ro, jddb_percona
```

### 数据库账号保留关键字
```
root，admin，os_admin，replicater，monitor，percona, admin, aurora, replicator, xtrabak, root, mysql, test, eagleye, information_schema, guest, add, analyze, asc, between, blob, call, change, check, condition, continue, cross, current_timestamp, database, day_microsecond, dec, default, desc, distinct, double, each, enclosed, exit, fetch, float8, foreign, goto, having, hour_minute, ignore, infile, insensitiv, int1, int4, interval, iterate, keys, leading, like, lines, localtimestamp, longblob, low_priority, mediumint, minute_microsecond, modifies, no_write_to_binlog, on, optionally, out, precision, purge, read, references, rename, require, revoke, schema, select, set, spatial, sqlexception, sql_big_result, ssl, table, tinyblob, to, true, unique, update, using, utc_timestamp, varchar, when, with, xor, all, and, asensitive, bigint, both, cascade, char, collate, connection, convert, current_date, current_user, databases, day_minute, decimal, delayed, describe, distinctrow, drop, else, escaped, explain, float, for, from, grant, high_priority, hour_second, in, inner, insert, int2, int8, into, join, kill, leave, limit, load, lock, longtext, match, mediumtext, minute_second, natural, null, optimize, or, outer, primary, raid0, reads, regexp, repeat, restrict, right, schemas, sensitive, show, specific, sqlstate, sql_calc_found_rows, starting, terminated, tinyint, trailing, undo, unlock, usage, utc_date, values, varcharacter, where, write, year_month, alter, as, before, binary, by, case, character, column, constraint, create, current_time, cursor, day_hour, day_second, declare, delete, deterministic, div, dual, elseif, exists, false, float4, force, fulltext, group, hour_microsecond, if, index, inout, int, int3, integer, is, key, label, left, linear, localtime, long, loop, mediumblob, middleint, mod, not, numeric, option, order, outfile, procedure, range, real, release, replace, return, rlike, second_microsecond, separator, smallint, sql, sqlwarning, sql_small_result, straight_join, then, tinytext, trigger, union, unsigned, use, utc_time, varbinary, varying, while, x509, zerofill, jcloud_yunding_db_push, jcloudv_push_rw, jcloudv_push_ro, jddbaclholder
```
