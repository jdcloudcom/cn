# 数据库本地备份

## 1.  检查数据库恢复模式
```commandline
use master;
go
select name,   case recovery_model
when 1 then   'Full'
when 2 then ' Bulk_logged   '
when 3 then   'Simple' end model from sys.databases
where name not   in ('master','tempdb','model','msdb');
go
```

**注意：数据库的恢复模式必须为Full**
- 如果model值不为Full，请执行步骤2
- 如果model值为Full，请执行步骤3

用户也可使用使用SQL Server Management Studio客户端工具对数据库进行完整备份，同样需确保数据库的恢复模式为“完整”
![本地备份1](../../../image/RDS/Backup-Local-Database-1.png)

## 2.将数据库的恢复模式设置为Full
```commandline
alter database [dbname] set recovery full;
go
```

重复步骤1，确认数据库恢复模式修改成功

## 3.  备份数据库
下面以备份文件名为testdb.bak为例：
```commandline
use master;
go
backup database [dbname] to disk   ='z:\Backup\testdb.bak' with compression,init,stats=5;
go
```
## 4. 校验备份文件的完整性
```commandline
use master;
go
restore filelistonly 
from disk = 'z:\backup\testdb.bak';
go
```
- 如果有结果集返回，则备份文件有效。
- 如果报错，则备份文件有误，请重新备份。



## 5.还原数据库的恢复模式
- 如变更过数据库的恢复模式，请执行如下命令，还原数据库的恢复模式；
- 如没有做过变更，则无需执行该步骤。
```commandline
alter database [dbname] set recovery [model];
go
```


## 6.    创建一个空数据库
最后，在云数据库上创建一个空库，用于备份文件导入。
用户也可使用使用SQL Server Management Studio客户端工具对数据库进行完整备份，同样需确保数据库的恢复模式为“完整”
