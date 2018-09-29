**使用限制**

**1. 暂不支持自增字段（auto_increment）**

DRDS暂时不支持自增字段auto_increment，用户需要在应用上自行实现数值自增的逻辑

**2. 不支持跨库事务**

DRDS 支持单个数据库事务，但不支持跨数据库的事务。

**3. 不支持跨库的join和子查询**

目前仅支持同一个数据库内的join和子查询语句，不支持跨库的join和子查询

**4. 不支持mysqldump**

DRDS自身不支持mysqldump，用户如果需要导出数据，可以直接登录到RDS MySQL上，对每个数据库逐一执行mysqldump操作
