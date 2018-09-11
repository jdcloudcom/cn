# 数据计算服务API


## 简介
数据计算服务相关API


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**cancelPySparkJob**|POST|终止用户PySpark脚本任务|
|**cancelRasQuery**|POST|终止用户Spark SQL脚本查询|
|**createDatabase**|POST|创建属于用户实例的数据库|
|**createTable**|POST|创建用户实例的数据表|
|**deleteDatabase**|DELETE|删除用户实例的指定数据库|
|**deleteTable**|DELETE|删除用户实例的指定数据表|
|**executePySparkQuery**|POST|执行用户编写的PySpark脚本|
|**executeRasQuery**|POST|执行用户编写的Spark SQL脚本|
|**getDatabaseInfo**|GET|查询用户实例的指定数据库信息|
|**getPySparkExecuteResult**|GET|获取用户PySpark脚本的执行结果|
|**getPySparkExecuteState**|GET|获取用户PySpark脚本的执行状态|
|**getRasQueryLog**|GET|获取用户Spark SQL脚本的查询日志|
|**getRasQueryResult**|GET|获取用户Spark SQL脚本的查询结果|
|**getRasQueryState**|GET|获取用户Spark SQL脚本的查询状态|
|**getTableInfo**|GET|查询用户实例的指定数据表信息|
|**listDatabaseInfo**|GET|查询用户实例的所有数据库信息|
|**listInstanceInfo**|GET|查询用户所属的实例信息|
|**listTableInfo**|GET|查询用户实例指定数据库下的所有数据表信息|
