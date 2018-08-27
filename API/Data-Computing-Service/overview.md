# 数据计算服务API


## 简介
数据计算服务相关API


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**cancelPySparkJob**|POST|终止PySpark任务|
|**cancelRasQuery**|POST|终止查询|
|**createDatabase**|POST|创建数据库|
|**createFile**|POST||
|**createNewFolder**|POST||
|**createTable**|POST|创建数据表|
|**deleteDatabase**|DELETE|删除数据库|
|**deleteFileOrFolder**|POST||
|**deleteTable**|DELETE|删除数据表|
|**executePySparkQuery**|POST|执行PySpark脚本|
|**executeRasQuery**|POST|执行Spark SQL|
|**fileCat**|GET||
|**getAclStatus**|GET||
|**getContentSummary**|GET||
|**getDatabaseInfo**|GET|查询数据库详情|
|**getFileStatus**|GET||
|**getFilesCount**|GET||
|**getHdfsRootPath**|GET||
|**getPySparkExecuteResult**|GET|获取PySpark执行的结果|
|**getPySparkExecuteState**|GET|获取PySpark脚本的执行状态|
|**getRasQueryLog**|GET|获取查询日志|
|**getRasQueryResult**|GET|获取查询的结果|
|**getRasQueryState**|GET|获取查询状态|
|**getTableInfo**|GET|查询数据表信息|
|**getXAttr**|GET||
|**getXAttrs**|GET||
|**initializeUserRootHdfsPathNotExist**|POST||
|**isExist**|GET||
|**listDatabaseInfo**|GET|查询数据库列表|
|**listFileAndFolders**|GET||
|**listFileAndFoldersOptional**|GET||
|**listFilesAndFolders**|GET||
|**listInstanceInfo**|GET|查询实例列表|
|**listTableInfo**|GET|查询指定数据库下所有数据表|
|**listUdfFileAndFolders**|GET||
|**modifyAclEntries**|POST||
|**removeAcl**|POST||
|**removeAclEntries**|POST||
|**removeDefaultAcl**|POST||
|**removeXAttr**|POST||
|**renameFile**|POST||
|**setAcl**|POST||
|**setOwner**|POST||
|**setPermission**|POST||
|**setPermissionByUGO**|POST||
|**setXAttr**|POST||
