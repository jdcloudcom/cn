## PostgreSQL日志
### 简介
目前接入日志服务的日志类型为慢查询日志，错误日志，审计日志。

### 字段说明
#### 慢查询日志
| 序号 | 字段名称 | 字段描述 | 字段类型 |
| --- | --- | --- | --- | 
| 1 | start_time  | 慢查询产生开始时间 | string |
| 2 | client_ip | 用户客户端ip地址 | string |
| 3 | user_name | 访问用户名称 | string |
| 4 | database_name | 请求访问数据库名称 | string |
| 5 | duration | 执行时长 | string |
| 6 | statement | 慢查询sql | string |

#### 错误日志
| 序号 | 字段名称 | 字段描述 | 字段类型 |
| --- | --- | --- | --- | 
| 1 | start_time  | 慢查询产生开始时间 | string |
| 2 | client_ip | 用户客户端ip地址 | string |
| 3 | user_name | 访问用户名称 | string |
| 4 | database_name | 请求访问数据库名称 | string |
| 5 | error_severity | 日志错误级别 | string |
| 6 | detail | 详细错误日志信息 | string |

#### 审计日志
| 序号 | 字段名称 | 字段描述 | 字段类型 |
| --- | --- | --- | --- | 
| 1 | start_time  | 审计日志产生开始时间 | string |
| 2 | client_ip | 用户客户端ip地址 | string |
| 3 | user_name | 访问用户名称 | string |
| 4 | database_name | 请求访问数据库名称 | string |
| 5 | command | 操作命令 | string |
| 6 | statement | 审计sql | string |
