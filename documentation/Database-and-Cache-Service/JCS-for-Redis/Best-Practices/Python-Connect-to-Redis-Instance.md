# Python连接
- step1：下载redis python客户端

 ```git clone https://github.com/andymccurdy/redis-py```
 
- step2：编写测试用例

```
#!/usr/bin/env python
#-*- coding: utf-8 -*-
import redis

#这里替换为连接的实例host和port
host = 'jredis-hb1-prod-957e3a3d-0d76-45d4-a896-706173208db2.jmiss.jcloud.com'
port = 6379

#这里配置token
token = 'B69B341E5C669082EFCF2E405C626379'

#连接时通过password参数指定AUTH信息
r = redis.StrictRedis(host=host, port=port, password=token)

#连接建立后就可以进行数据库操作，详情文档参考https://github.com/andymccurdy/redis-py
r.set('foo', 'bar');
print r.get('foo')
```
