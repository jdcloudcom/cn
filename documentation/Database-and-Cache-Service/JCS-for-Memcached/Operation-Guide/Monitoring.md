# 实例监控
缓存Memcached目前提供26个监控指标，查看监控步骤为：

1. 登录 [Memcached 控制台](https://memcached-console.jdcloud.com/redis) ，定位目标实例

2. 点击实例名称进入实例详情页面

3. 在上方导航Tab页中，选择监控

4. 选择监控时间进行查看

5. 右上角可设置报警规则，可点击进入云监控报警规则页面

## 监控时间范围：
采样数据最小周期为2分钟，展示时长有最近1小时、6小时、12小时、1天、3天、7天和14天，还可自己选择日期范围（30天内）。如果想查看更加详细的监控指标数据，请在云监控菜单进行查看

## 监控指标
序号|监控项|英文说明|单位
:---|:--|:--|:---
1|当前连接数|	curr_connections|	个
2	|拒绝连接数	|rejected_connections	|次
3|	出入口流量|	OutFlow and InFlow	|MB/s
4|	发送总字节数|	bytes_written	|Byte
5	|读取总字节数	|bytes_read	|Byte
6	|存储占用字节数|	Storage occupancy bytes|	Byte
7	|存储数据总数	|curr_items	|个
8	|lru淘汰的item数|	evictions	|个
9	|CPU使用率	|CPU Usage|	%
10|	get命令命中次数|	get_hits|	次
11	|get命令未命中次数|	get_misses	|次
12|	get命令使用次数|	cmd_get|	次
13	|delete命令命中次数	|delete_hits|次
14|	delete命令未命中次数	|delete_misses|	次
15	|incr命令命中次数	|incr_hits	|次
16|	incr命令未命中次数	|incr_misses	|次
17	|decr命令命中次数|	decr_hits	|次
18|	decr命令未命中次数|	decr_misses	|次
19|	cas命令命中次数|	cas_hits	|次
20	|cas命令未命中次数|	cas_misses	|次
21|	touch命令成功修改生命周期的次数|	touch_hits|	次
22	|touch命令没有找到item的次数|	touch_misses	|次
23|	认证命令处理的次数|	auth_cmds|	次
24|	认证失败数目	|auth_errors	|次
25|	set命令使用次数|	cmd_set	|次
26	|flush命令请求次数|	cmd_flush	|次
