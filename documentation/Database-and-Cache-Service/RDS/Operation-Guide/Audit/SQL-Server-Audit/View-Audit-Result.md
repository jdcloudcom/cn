# 查看审计文件内容

SQL Server生成的审计文件是二进制格式的，可通过SQL Server内置函数fn_get_audit_file查看，具体步骤如下：

1. 将审计结果文件下载到安装有SQL Server的服务器上，注意高版本的SQL Server可以兼容低版本的审计文件，反之则不行。 例如在SQL Server 2014上可以查看2014， 2012，2008R2生成的审计文件，但不能查看2016的审计文件
2. 连接到master数据库
3. 执行以下SQL（假设审计文件为‘D:\audit\RDSAudit_131702498897960000.sqlaudit’）
```commandline
select * from sys.fn_get_audit_file('D:\audit\RDSAudit_131702498897960000.sqlaudit',NULL, NULL)
```
4. 详细的SQL语法和查询结果含义可参见以下微软的官方文档：
- [2008R2](https://docs.microsoft.com/zh-cn/previous-versions/sql/sql-server-2008-r2/cc280765%28v%3dsql.105%29)
- [2012](https://docs.microsoft.com/zh-cn/previous-versions/sql/sql-server-2012/cc280765%28v%3dsql.110%29)
- [2014](https://technet.microsoft.com/zh-cn/library/cc280765(v=sql.120).aspx)
- [2016](https://docs.microsoft.com/zh-cn/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql?view=sql-server-2016)

