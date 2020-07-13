# 枚举类型定义

- engine RDS引擎类型
- engineVersion RDS引擎版本
- instanceStatus 实例状态
- dbStatus 数据库状态
- accountStatus 账号状态
- privilege 数据库访问权限
- characterSetName 数据库字符集
- sqlAuditStatus 数据审计状态
- connectionMode 访问模式
- backupStatus 备份状态
- backupType 备份类型
- backupMode 备份模式
- backupUnit 备份粒度
- instanceClass 实例规格
- parameterGroupStatus 参数组状态
- parameterStatus 参数状态
- instanceType 实例类型
- instanceStorageType 存储类型
- Audit 操作类型
- logType 日志文件类型
- loadBalancerPolicy 读写分离代理后端实例负载均衡策略
- backendType 读写分离代理后端实例的配置方式
- readWriteProxyStatus 读写分离代理状态

## engine RDS引擎类型

|取值|说明|
|-|-|
|MySQL|MySQL数据库引擎|
|MariaDB|MariaDB数据库引擎|
|Percona|Percona数据库引擎|
|SQL Server|SQL Server数据库引擎，注意中间有空格|
|PostgreSQL|PostgreSQL数据库引擎|

## engineVersion RDS引擎版本

|取值|说明|
|-|-|
|5.5|MySQL 5.5 版本|
|5.6|MySQL 5.6 版本|
|5.7|MySQL 5.7 版本|
|5.7|Percona 5.7 版本|
|10.2|MariaDB 10.2 版本|
|2008R2 EE|SQL Server 2008R2 企业版|
|2012 EE|SQL Server 2012 企业版|
|2014 EE|SQL Server 2014 企业版|
|2016 EE|SQL Server 2016 企业版|
|2012 SE|SQL Server 2012 标准版|
|2014 SE|SQL Server 2014 标准版|
|2016 SE|SQL Server 2016 标准版|
|2012 Web|SQL Server 2012 Web版|
|2014 Web|SQL Server 2014 Web版|
|2016 Web|SQL Server 2016 Web版|
|9.6|PostgreSQL 9.6版本|
|10.6|PostgreSQL 10.6版本|
|11.2|PostgreSQL 11.2版本|
|12.2|PostgreSQL 12.2版本|

## instanceStatus 实例状态

|取值|说明|
|-|-|
|BUILDING|创建中|
|RUNNING|运行|
|DELETING|删除中|
|FAILOVER|主备切换中|
|RESTORING|本地覆盖恢复中|
|DB_RESTORING|单库备份恢复中|
|MODIFYING|变配中|
|BUILD_READONLY|新增只读实例中|
|REBOOTING|重启中|
|MAINTENANCE|维护中|
|AZ_MIGRATING|可用区迁移中|
|DDLING|DDL 变更中|
|PARAMETERGROUP_MODIFYING|修改参数组中|
|AUDIT_OPENING|开启审计中|
|AUDIT_CLOSING|关闭审计中|
|SECURITY_OPENING|开启高安全模式中|
|SECURITY_CLOSING|关闭高安全模式中|
|SSL_OPENING|开启SSL加密模式中|
|SSL_CLOSING|关闭SSL加密模式中|

## dbStatus 数据库状态

|取值|说明|
|-|-|
|BUILDING|创建中|
|RUNNING|运行|
|DELETING|删除中|

## accountStatus 账号状态

|取值|说明|
|-|-|
|BUILDING|创建中|
|RUNNING|运行|
|DELETING|删除中|

## privilege 数据库访问权限

|取值|说明|
|-|-|
|ro|只读|
|rw|读写|

## characterSetName 数据库字符集

|取值|说明|
|-|-|
|utf8|MySQL, Percona, MariaDB，PostgreSQL字符集|
|gbk|MySQL, Percona, MariaDB，PostgreSQL字符集|
|latin1|MySQL, Percona, MariaDB，PostgreSQL字符集|
|utf8mb4|MySQL, Percona, MariaDB字符集|
|Chinese_PRC_CI_AS|SQL Server字符集|
|Chinese_PRC_CS_AS|SQL Server字符集|
|SQL_Latin1_General_CP1_CI_AS|SQL Server字符集|
|SQL_Latin1_General_CP1_CS_AS|SQL Server字符集|
|Chinese_PRC_BIN|SQL Server字符集|

## sqlAuditStatus 数据审计状态

|取值|说明|
|-|-|
|off|关闭（默认）|
|on|开启|

## connectionMode 访问模式

|取值|说明|
|-|-|
|standard|标准访问模式(默认)|
|security|高安全访问模式|

## backupStatus 备份状态

|取值|说明|
|-|-|
|COMPLETED|备份成功|
|ERROR|备份错误|
|BUILDING|备份中|
|DELETING|删除中|

## backupType 备份类型

|取值|说明|
|-|-|
|full|全量备份|
|diff|增量备份|

## backupMode 备份模式

|取值|说明|
|-|-|
|auto|系统自动备份|
|manual|手动备份|

## backupUnit 备份粒度

|取值|说明|
|-|-|
|instance|实例备份|
|database|数据库备份|

## instanceClass  实例规格
- SQL Server

|	instanceClass	|	CPU(核)	|	内存(GB)	|	磁盘(GB)	|
|	-	|	-	|	-	|	-	|
|	db.sqlsvr.s1.large	|	2	|	8	|	200	|
|		|	2	|	8	|	300	|
|		|	2	|	8	|	400	|
|		|	2	|	8	|	500	|
|	db.sqlsvr.s1.xlarge	|	4	|	16	|	400	|
|		|	4	|	16	|	500	|
|		|	4	|	16	|	600	|
|		|	4	|	16	|	800	|
|	db.sqlsvr.s1.2xlarge	|	8	|	32	|	600	|
|		|	8	|	32	|	800	|
|		|	8	|	32	|	1000	|
|		|	8	|	32	|	1200	|
|	db.sqlsvr.s1.4xlarge	|	16	|	64	|	1000	|
|		|	16	|	64	|	1200	|	|
|		|	16	|	64	|	1600	|	|
|		|	16	|	64	|	2000	|	|

- MySQL

|	instanceClass	|	CPU(核)	|	内存(GB)	|	磁盘(GB)	|
|	---	|	---	|	---	|	---	|
|	db.mysql.s1.micro	|	1	|	1	|	20	|
|		|	1	|	1	|	40	|
|		|	1	|	1	|	60	|
|		|	1	|	1	|	80	|
|		|	1	|	1	|	100	|
|	db.mysql.s1.small	|	1	|	2	|	60	|
|		|	1	|	2	|	80	|
|		|	1	|	2	|	100	|
|		|	1	|	2	|	120	|
|		|	1	|	2	|	150	|
|	db.mysql.s1.medium	|	1	|	4	|	100	|
|		|	1	|	4	|	120	|
|		|	1	|	4	|	150	|
|		|	1	|	4	|	200	|
|		|	1	|	4	|	300	|
|	db.mysql.s1.large	|	2	|	8	|	200	|
|		|	2	|	8	|	250	|
|		|	2	|	8	|	300	|
|		|	2	|	8	|	400	|
|		|	2	|	8	|	500	|
|	db.mysql.s1.xlarge	|	4	|	16	|	400	|
|		|	4	|	16	|	500	|
|		|	4	|	16	|	600	|
|		|	4	|	16	|	800	|
|		|	4	|	16	|	1000	|
|	db.mysql.s1.2xlarge	|	8	|	32	|	600	|
|		|	8	|	32	|	800	|
|		|	8	|	32	|	1000	|
|		|	8	|	32	|	1200	|
|		|	8	|	32	|	1600	|
|	db.mysql.s1.4xlarge	|	16	|	64	|	1000	|
|		|	16	|	64	|	1200	|
|		|	16	|	64	|	1600	|
|		|	16	|	64	|	2000	|

- PostgreSQL

|	instanceClass	|	CPU(核)	|	内存(GB)	|	磁盘(GB)	|
|	---	|	---	|	---	|	---	|
|	db.pg.s1.micro	|	1	|	1	|	20	|
|		|	1	|	1	|	40	|
|		|	1	|	1	|	60	|
|		|	1	|	1	|	80	|
|		|	1	|	1	|	100	|
|	db.pg.s1.small	|	1	|	2	|	60	|
|		|	1	|	2	|	80	|
|		|	1	|	2	|	100	|
|		|	1	|	2	|	120	|
|		|	1	|	2	|	150	|
|	db.pg.s1.medium	|	1	|	4	|	100	|
|		|	1	|	4	|	120	|
|		|	1	|	4	|	150	|
|		|	1	|	4	|	200	|
|		|	1	|	4	|	300	|
|	db.pg.s1.large	|	2	|	8	|	200	|
|		|	2	|	8	|	250	|
|		|	2	|	8	|	300	|
|		|	2	|	8	|	400	|
|		|	2	|	8	|	500	|
|	db.pg.s1.xlarge	|	4	|	16	|	400	|
|		|	4	|	16	|	500	|
|		|	4	|	16	|	600	|
|		|	4	|	16	|	800	|
|		|	4	|	16	|	1000	|
|	db.pg.s1.2xlarge	|	8	|	32	|	600	|
|		|	8	|	32	|	800	|
|		|	8	|	32	|	1000	|
|		|	8	|	32	|	1200	|
|		|	8	|	32	|	1600	|
|	db.pg.s1.4xlarge	|	16	|	64	|	1000	|
|		|	16	|	64	|	1200	|
|		|	16	|	64	|	1600	|
|		|	16	|	64	|	2000	|
## parameterStatus 参数状态 
|取值|说明|
|-|-|
|VALID|生效|
|SYNCING|同步中|
|PENDING_REBOOT|待重启|

## parameterGroupStatus 参数组状态 
|取值|说明|
|-|-|
|AVAILABLE|可用|
|SYNCING|同步中|

## instanceType 实例类型 
|取值|说明|
|-|-|
|standalone|单实例|
|cluster|主备实例|
|readonly|只读实例|

## instanceStorageType 存储类型 
|取值|说明|
|-|-|
|LOCAL_SSD|本地SSD|
|LOCAL_NVME|本地NVME|
|EBS_SSD|SSD云盘|

## audit 操作类型 
|取值|说明|
|-|-|
|QUERY|查询|
|DML|DML|
|DDL|DDL|
|CONNECT|连接|
|DISCONNECT|断开连接|
|FAILED_CONNECT|错误连接|

## logType 日志文件类型 
|取值|说明|
|-|-|
|ERROR_LOG|错误日志|
|SLOW_LOG|慢日志|

## loadBalancerPolicy 读写分离代理后端实例负载均衡策略
|取值|说明|
|-|-|
|LEAST_ROUTER_CONNECTIONS|最少连接数|
|LEAST_BEHIND_MASTER|最少同步延迟|
|LEAST_CURRENT_OPERATIONS|最少活跃连接数|
|ADAPTIVE_ROUTING|平均响应时延|

## readWriteProxyStatus 读写分离代理后端状态
|取值|说明|
|-|-|
|INITIALIZING|初始化中|
|RUNNING|运行|
|DELETING|删除中|
|RESETTING|重置中|

## mysql 数据库全局权限信息 
|取值|说明|
|-|-|
|ALL|包括以下全部权限|
|EVENT|Enables use of statements that create, alter, drop, or display events for the Event Scheduler|
|EXECUTE|Enables use of statements that execute stored routines (stored procedures and functions)|
|GRANT OPTION|Enables you to grant to or revoke from other users those privileges that you yourself possess|
|LOCK TABLES|Enables use of explicit LOCK TABLES statements to lock tables for which you have the SELECT privilege|
|REFERENCES|Creation of a foreign key constraint requires the REFERENCES privilege for the parent table|
|ALTER|Enables use of the ALTER TABLE statement to change the structure of tables|
|CREATE VIEW|Enables use of the CREATE VIEW statement|
|CREATE|Enables use of statements that create new databases and tables|
|DELETE|Enables rows to be deleted from tables in a database|
|DROP|Enables use of statements that drop (remove) existing databases, tables, and views|
|INDEX|Enables use of statements that create or drop (remove) indexes|
|INSERT|Enables rows to be inserted into tables in a database|
|SELECT|Enables rows to be selected from tables in a database|
|SHOW VIEW|Enables use of the SHOW CREATE VIEW statement|
|TRIGGER|Enables trigger operations|
|UPDATE|Enables rows to be updated in tables in a database|
|ALTER ROUTINE|Enables use of statements that alter or drop stored routines (stored procedures and functions)|
|CREATE TEMPORARY TABLES|Enables the creation of temporary tables using the CREATE TEMPORARY TABLE statement|
|CREATE ROUTINE|Enables use of statements that create stored routines (stored procedures and functions)|
|PROCESS|Enables display of information about the threads executing within the server (that is, information about the statements being executed by sessions)|
|SHOW DATABASES|Enables the account to see database names by issuing the SHOW DATABASE statement|
|REPLICATION SLAVE|Enables the account to request updates that have been made to databases on the master server, using the SHOW SLAVE HOSTS, SHOW RELAYLOG EVENTS, and SHOW BINLOG EVENTS statements|
|REPLICATION CLIENT|Enables use of the SHOW MASTER STATUS, SHOW SLAVE STATUS, and SHOW BINARY LOGS statements|

## mysql 数据库权限信息 
|取值|说明|
|-|-|
|ALL|包括以下全部权限|
|EVENT|Enables use of statements that create, alter, drop, or display events for the Event Scheduler|
|EXECUTE|Enables use of statements that execute stored routines (stored procedures and functions)|
|GRANT OPTION|Enables you to grant to or revoke from other users those privileges that you yourself possess|
|LOCK TABLES|Enables use of explicit LOCK TABLES statements to lock tables for which you have the SELECT privilege|
|REFERENCES|Creation of a foreign key constraint requires the REFERENCES privilege for the parent table|
|ALTER|Enables use of the ALTER TABLE statement to change the structure of tables|
|CREATE VIEW|Enables use of the CREATE VIEW statement|
|CREATE|Enables use of statements that create new databases and tables|
|DELETE|Enables rows to be deleted from tables in a database|
|DROP|Enables use of statements that drop (remove) existing databases, tables, and views|
|INDEX|Enables use of statements that create or drop (remove) indexes|
|INSERT|Enables rows to be inserted into tables in a database|
|SELECT|Enables rows to be selected from tables in a database|
|SHOW VIEW|Enables use of the SHOW CREATE VIEW statement|
|TRIGGER|Enables trigger operations|
|UPDATE|Enables rows to be updated in tables in a database|
|ALTER ROUTINE|Enables use of statements that alter or drop stored routines (stored procedures and functions)|
|CREATE TEMPORARY TABLES|Enables the creation of temporary tables using the CREATE TEMPORARY TABLE statement|
|CREATE ROUTINE|Enables use of statements that create stored routines (stored procedures and functions)|


## mysql 数据库表权限信息 
|取值|说明|
|-|-|
|ALL|包括以下全部权限|
|REFERENCES|Creation of a foreign key constraint requires the REFERENCES privilege for the parent table|
|ALTER|Enables use of the ALTER TABLE statement to change the structure of tables|
|CREATE VIEW|Enables use of the CREATE VIEW statement|
|CREATE|Enables use of statements that create new databases and tables|
|DELETE|Enables rows to be deleted from tables in a database|
|DROP|Enables use of statements that drop (remove) existing databases, tables, and views|
|INDEX|Enables use of statements that create or drop (remove) indexes|
|INSERT|Enables rows to be inserted into tables in a database|
|SELECT|Enables rows to be selected from tables in a database|
|SHOW VIEW|Enables use of the SHOW CREATE VIEW statement|
|TRIGGER|Enables trigger operations|
|UPDATE|Enables rows to be updated in tables in a database|
