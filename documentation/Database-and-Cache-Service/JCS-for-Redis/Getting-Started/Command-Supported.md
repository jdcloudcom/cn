# Redis命令支持



云数据库Redis基于2.8.19版本，命令请参见：http://redis.io/commands



## 支持的命令操作

Key(键)|String(字符串)|Hash（哈希表）|List（列表）|Set（集合）|SortedSet（有序集合） 
---|:--:|:--:|:--:|:--:|---:
DEL|APPEND|HDEL|LINDEX|SADD|ZADD            
DUMP|BITCOUNT|HEXISTS|LINSERT|SCARD|ZCARD            
EXISTS|BITPOS|HGET|LLEN|SISMEMBER|ZCOUNT            
EXPIRE| DECR |HGETALL  | LPOP  |      	SMEMBERS     |ZINCRBY            
EXPIREAT   |         	DECRBY       |     	HINCRBY       |     	LPUSH       |     	SPOP      | ZRANGE            
KEYS*   |               	GET      |      	HINCRBYFLOAT   |         	LPUSHX   |         	SRANDMEMBER          |ZRANGEBYSCORE            
PERSIST    |        	GETBIT        |    	HKEYS         |   	LRANGE       |     	SREM     |ZRANK            
PEXPIRE   |         	GETRANGE      |      	HLEN        |    	LREM        |    	SSCAN      | ZREM            
PEXPIREAT         |   	GETSET        |    	HMGET       |     	LSET         |   	|ZREMRANGEBYRANK            
PTTL|INCR|HMSET|LTRIM | |        	ZREMRANGEBYSCORE            
RESTORE|INCRBY|HSET|RPOP      | |      	ZREVRANGE            
SORT|INCRBYFLOAT|HSETNX|RPUSH  | |          	ZREVRANGEBYSCORE            
TTL|MGET|HVALS|RPUSHX     | |       	ZREVRANK            
TYPE|MSET|HSCAN| | |       	       	ZSCORE            
SCAN|PSETEX| | | |ZSCAN            
| |SET   | |  |       	|ZRANGEBYLEX            
| |SETBIT      | | |   |   	ZLEXCOUNT            
| |SETEX       | | |    | 	ZREMRANGEBYLEX            
| |SETNX| | | | |             	
| |SETRANGE   | | | |         	
| |STRLEN    | | | |        	

以及

Connection（连接）|Server（服务器）|Scripting(脚本)     
---|:--:|---:
AUTH|INFO*|EVAL            
PING|CONFIG GET*|SCRIPT EXISTS            
QUIT|FLUSHDB|EVALSHA            
ECHO| |SCRIPT FLUSH            
| | |SCRIPT KILL            
| | |SCRIPT LOAD  

说明：

- KEYS命令，只能在VPC网络下使用，属于危险的命令，可能造成性能问题，请确保在key很少的情况下使用。如果需要从一个大数据集中查找特定的 key ，推荐使用 Redis 的集合结构(set)

- INFO命令，在集群版中使用受限：不支持 info cpu/replication/persistence

- CONFIG GET命令，在集群版中返回参数暂时未进行叠加

暂未开放的命令

Key(键)|String(字符串)|List（列表）|Set（集合）|SortedSet（有序集合） |Connection（连接）|Server（服务器）
---|:--:|:--:|:--:|:--:|:--:|---:
RANDOMKEY|BITOP|BLPOP|SDIFF|ZUNIONSTORE|SELECT|FLUSHALL            
RENAME|MSETNX|BRPOP|SDIFFSTORE|ZINTERSTORE| |DBSIZE
RENAMENX| |BRPOPLPUSH  |SINTER| | |TIME            
OBJECT| | RPOPLPUSH|SINTERSTORE| | |MONITOR            
MIGRATE | | | SMOVE | | | SLOWLOG            
| | | |SUNION | | |BGREWRITEAOF            
| | | |SUNIONSTORE| | |BGSAVE            
| | | | | | |CONFIG REWRITE            
| | | | | | |CONFIG SET            
| | | | | | |CONFIG RESETSTAT            
| | | | | | |COMMAND            
| | | | | | |COMMAND COUNT            
| | | | | | |COMMAND GETKEYS            
| | | | | | |COMMAND INFO            
| | | | | | |DEBUG OBJECT            
| | | | | | |DEBUG SEGFAULT            
| | | | | | |LASTSAVE            
| | | | | | |ROLE            
| | | | | | |SAVE            
| | | | | | |SHUTDOWN            
| | | | | | |SLAVEOF            
| | | | | | |SYNC            
| | | | | | |PSYNC  

以及

HyperLog|LogPub/Sub（发布/订阅）|Transaction（事务）| Geo(地理位置)      
---|:--:|:--:|---:
PFADD|PSUBSCRIBE|DISCARD|GEOADD            
PFCOUNT|PUBLISH|EXEC|GEOHASH            
PFMERGE|PUBSUB|MULTI|GEOPOS            
| |PUNSUBSCRIBE|UNWATCH|GEODIST            
| |SUBSCRIBE|WATCH|GEORADIUS            
| |UNSUBSCRIBE| |GEORADIUSBYMEMBER  

集群实例不支持的命令

Connection（连接）|Server（服务器）|Scripting(脚本)
---|:--:|---:
ECHO|CLIENT KILL|EVALSHA            
| |CLIENT LIST|SCRIPT EXISTS            
| |CLIENT GETNAME|SCRIPT FLUSH            
| |CLIENT SETNAME|SCRIPT KILL
| | |SCRIPT LOAD            
