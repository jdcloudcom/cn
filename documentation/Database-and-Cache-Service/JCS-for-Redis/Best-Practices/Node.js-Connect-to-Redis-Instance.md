# Node.js连接

- step1：下载安装Node.js的Redis客户端

```
git clone https://github.com/NodeRedis/node_redisnpm install redis
```

- step2：调用示例代码

```
//连接redis
var redis = require("redis"),
  port = 6379,
  host = 'jredis-hb1-prod-957e3a3d-0d76-45d4-a896-706173208db2.jmiss.jcloud.com',
  token = 'B69B341E5C669082EFCF2E405C626379',
  opts = {no_ready_check:true},//设置项：由于ready_check打开会发送info命令检查redis是否可用，Jmiss AP暂不支持info命令，请配置该项为true，否则AP会关闭该连接
  client = redis.createClient(port, host, opts);

// AUTH
client.auth(token, redis.print)

// 写入数据
client.set("key", "OK");

// 获取数据，返回String
client.get("key", function (err, reply) {
    console.log(reply.toString());
});

// 如果传入一个Buffer，返回也是一个Buffer
client.get(new Buffer("key"), function (err, reply) {
    console.log(reply.toString());
});
client.quit();
```
