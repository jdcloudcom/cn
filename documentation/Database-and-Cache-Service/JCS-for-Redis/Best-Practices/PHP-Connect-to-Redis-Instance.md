# PHP连接
- step1：下载php redis客户端 参考地址：https://github.com/phpredis/phpredis

- step2：编写测试用例

```
<?php
  /* 这里替换为连接的实例host和port */
  $host = "jredis-hb1-prod-957e3a3d-0d76-45d4-a896-706173208db2.jmiss.jcloud.com";
  $port = 6379;
  /* 这里替换为集群的token */
  $token = "B69B341E5C669082EFCF2E405C626379";

  $redis = new Redis();
  if ($redis->connect($host, $port) == false) {
    die($redis->getLastError());
  }
  /* 使用token作为AUTH的密码 */
  if ($redis->auth($token) == false) {
    die($redis->getLastError());
  }
  /* 认证后就可以进行数据库操作，详情文档参考https://github.com/phpredis/phpredis */
  if ($redis->set("foo", "bar") == false) {
    die($redis->getLastError());
  }
  $value = $redis->get("foo");
  echo $value;
?>
```
