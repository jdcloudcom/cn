# 续费管理


## 简介
续费管理相关接口


### 版本
v2


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**queryInstance**|POST|提供可续费的实例信息查询。|
|**renewInstance**|POST|对相关实例进行续费。调用该接口会创建一个续费订单，并自动扣除您账户可用代金券和余额完成支付，如因为某些原因支付失败，订单会自动取消。|
|**setRenewal**|PUT|为一个或多个实例设置自动续费服务。|

## 公共参数说明
<table><tr><th>业务线</th><th>产品线</th><th>产品线名称</th></tr><tr><td rowspan="20">jcloud</td><td>vm</td><td>云主机</td></tr><tr><td>rds</td><td>云数据库 RDS</td></tr><tr><td><span>mongodb</span></td><td>云数据库 MongoDB</td></tr><tr><td>ip</td><td>公网IP</td></tr><tr><td>disk</td><td>云硬盘</td></tr><tr><td>redis</td><td>缓存Redis</td></tr><tr><td>ipanti</td><td>IP 高防</td></tr><tr><td>sgw</td><td>应用安全网关</td></tr><tr><td>waf</td><td>Web 应用防火墙</td></tr><tr><td>antipro</td><td>DDoS 防护包</td></tr><tr><td>jdworkspace</td><td>云桌面</td></tr><tr><td>memcached</td><td>云缓存 Memcached</td></tr><tr><td>jdworkspacebw</td><td>云桌面公网带宽</td></tr><tr><td>csa</td><td>态势感知</td></tr><tr><td>domainservice</td><td>云解析</td></tr><tr><td>pod</td><td>原生容器Pod</td></tr><tr><td>nativecontainer</td><td>原生容器实例</td></tr><tr><td>jdw</td><td>数据仓库</td></tr><tr><td>es</td><td>云搜索</td></tr><tr><td>drds</td><td>分布式关系型数据库 DRDS</td></tr><tr><td rowspan="4">aidc</td><td>edcpseip</td><td>边缘云公网IP</td></tr><tr><td>edcps</td><td>分布式云物理服务器</td></tr><tr><td>cpseip</td><td>物理云公网IP</td></tr><tr><td>cps</td><td>云物理服务器</td></tr><tr><td rowspan="9">yunding</td><td>yd-vm</td><td>云鼎云主机</td></tr><tr><td>yd-disk</td><td>云鼎云硬盘</td></tr><tr><td>yd-ip</td><td>云鼎公网IP</td></tr><tr><td>yd-sqlserver</td><td>云鼎云数据库 SQL Server</td></tr><tr><td>yd-antipro</td><td>云鼎DDoS 防护包</td></tr><tr><td>yd-csa</td><td>云鼎态势感知</td></tr><tr><td>yd-redis</td><td>云鼎云缓存 Redis</td></tr><tr><td>yd-sgw</td><td>云鼎应用安全网关</td></tr><tr><td>yd-database</td><td>云鼎云数据库 MySQL</td></tr><tr><td rowspan="5">ccy</td><td>ccyredis</td><td>产创云云缓存Redis</td></tr><tr><td>ccydatabase</td><td>产创云云数据库MySQL</td></tr><tr><td>ccydisk</td><td>产创云云硬盘</td></tr><tr><td>ccyip</td><td>产创云公网IP</td></tr><tr><td>ccyvm</td><td>产创云云主机</td></tr></table>
