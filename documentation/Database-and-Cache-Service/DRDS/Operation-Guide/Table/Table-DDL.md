# 表DDL语法

原先DRDS创建表时，需要先通过控制台定义表的拆分信息，然后在通过SQL创建表。 这种方式操作相对麻烦，用户需要分别通过控制台和SQL进行操作。因此DRDS新版本对此进行了改进，可直接通过SQL语句创建拆分表。


## 创建表的SQL语法
```SQL
CREATE TABLE table_name
 (create_definition,...)
 [DRDS partition options]
 
 DRDS partition options:
 dbpartition by
     INT_MOD([column_name])    -- 整型字段的拆分
     | STRING_HASH([column_name])    -- 字符字段的拆分，
     | YYYYMM([column_name]) | YYYY([column_name]) START([start_date]) period [num]  -- 时间字段的拆分，按年或月拆分，从start_date开始，每[num]个月一个分表     
```
   
## 拆分函数
目前DRDS支持以下的拆分函数，函数名均不区分大小写
- INT_MOD(): 对整型字段进行拆分
- STRING_HASH()：对字符字段进行拆分
- YYYYMM()：对时间，日期字段进行拆分，按月拆分
- YYYY()：时间，日期字段进行拆分，按年拆分
