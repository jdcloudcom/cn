## JDW数据仓库日志
### 简介
目前接入日志服务的日志类型为审计日志。

### 字段说明
#### 审计日志
| 序号 | 字段名称 | 字段描述 | 字段类型 |
| --- | --- | --- | --- | 
| 1 | start_time  | 审计日志产生开始时间 | string |
| 2 | client_ip | 用户客户端ip地址 | string |
| 3 | user_name | 访问用户名称 | string |
| 4 | database_name | 请求访问数据库名称 | string |
| 5 | thread_id | 线程ID | string |
| 6 | statement | 审计sql | string |
