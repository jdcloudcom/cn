# 连接实例

由于Jmiss Redis 提供的数据库服务与原生的数据库服务完全兼容，连接数据库的方式也基本类似。任何兼容 Redis 协议的客户端都可以访问Jmiss Redis 服务，用户可以根据自身应用特点选用任何 Redis 客户端。


# 京东云主机Redis-cli连接

京东云缓存Redis仅支持京东云VPC访问，即只有在相同VPC中的云主机上安装Redis，才能使用Redis-cli与缓存Redis建立连接并进行数据操作。

说明：在京东云主机上安装 Redis 的命令请参考 Redis 官方网页。

## Redis-cli 连接缓存Redis 的命令如下：

redis-cli -h [host] -p [port] -a [token]

说明：redis-cli -h 访问域名 -p 默认端口 -a 连接密码

示例：redis-cli -h jredis-cn-north-1-prod-redis-a90ng7vk5t.jdcloud.com -p 6379 -a redis-a90ng7vk5t:password

参考链接：https://redis.io/topics/rediscli

