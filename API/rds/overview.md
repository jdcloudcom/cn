# 云数据库RDS


## 简介
目前RDS OpenAPI支持云数据库SQL Server，可以通过OpenAPI实现数据库管理，账号管理，备份管理，单库上云等功能，后续将支持云数据库MySQL


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**createAccount**|POST|创建数据库账户&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**createAudit**|POST|开启数据库审计&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**createBackup**|POST|创建备份&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**createDatabase**|POST|创建数据库&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**createInstance**|POST|创建数据库集群实例&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：支持|
|**deleteAccount**|DELETE|删除数据库账户&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**deleteAudit**|DELETE|清除/关闭 数据库审计&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**deleteBackup**|DELETE|删除备份&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**deleteDatabase**|DELETE|删除数据库&lt;/br&gt;敏感操作，可开启&lt;a href=&quot;https://www.jdcloud.com/help/detail/3786/isCatalog/1&quot;&gt;MFA操作保护&lt;/a&gt;|
|**deleteInstance**|DELETE|删除数据库集群实例及Mysql只读实例&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：支持&lt;/br&gt;敏感操作，可开启&lt;a href=&quot;https://www.jdcloud.com/help/detail/3786/isCatalog/1&quot;&gt;MFA操作保护&lt;/a&gt;|
|**describeAccounts**|GET|查看实例下所有账号信息&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**describeAudit**|GET|查看开启的审计选项&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**describeBackupDownloadURL**|GET|获取备份下载链接&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**describeBackups**|GET|获取备份信息&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**describeDatabases**|GET|查看数据库列表&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**describeErrorLogs**|GET|获取SQL Server 错误日志及下载信息&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**describeImportFiles**|GET|获取单库上云文件列表&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**describeIndexPerformance**|POST|索引性能统计&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**describeInstanceAttributes**|GET|查询RDS实例详细信息&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：支持|
|**describeInstances**|GET|查询RDS实例列表&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：支持|
|**describeQueryPerformance**|POST|查询性能统计&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**failoverInstance**|POST|RDS实例主备切换&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**getAuditDownloadURL**|POST|获取某个审计文件的下载链接&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**getAuditFiles**|POST|查看审计文件列表&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**getAuditOptions**|POST|获取审计所有选项及推荐的选项&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**getUploadKey**|POST|获取上传导入文件的需要的Key&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**grantPrivilege**|POST|数据库账号授权&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**modifyAudit**|POST|修改当前审计选项&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**rebootInstance**|POST|重启RDS实例&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**resetPassword**|POST|数据库账号重置密码&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**restoreDatabaseFromBackup**|POST|从云数据库SQL Server备份中恢复单个数据库&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**restoreDatabaseFromFile**|POST|从用户上传的备份文件中恢复SQL Server数据库&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**restoreDatabaseFromOSS**|POST|从OSS恢复SQL Server数据库&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**setImportFileShared**|POST|设置上传文件是否共享给该用户的其他实例&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
|**setInstanceName**|POST|修改RDS实例名称&lt;/br&gt;- SQL Server：支持&lt;/br&gt;- MySQL：暂不支持|
