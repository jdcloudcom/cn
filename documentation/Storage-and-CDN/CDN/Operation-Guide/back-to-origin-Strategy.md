# 回源策略

添加域名后，点击【加速域名】进入域名配置基本信息，可输入【回源配置】信息，回源方式分为IP回源、域名回源、oss回源三种。

![image.png](https://img1.jcloudcs.com/cms/cf317c03-b662-4a37-a564-cee61f253fa220180118102313.png)                                               

**IP回源**

![image.png](https://img1.jcloudcs.com/cms/4b305baa-c773-4922-9cd7-b7afc64cd44d20180118102439.png)

l  回源IP最多可支持10个IP回源，回源的权重等比分配，CDN自动依次按IP列表顺序轮询回源，达到均衡回源的效果。

l  IP回源支持主备回源，在主源没有响应的情况下会自动回备源请求内容。

**域名回源**

![image.png](https://img1.jcloudcs.com/cms/c9c40a4e-2042-47bd-98f6-4cce01c3284f20180118102533.png)

l  域名回源最多可配置5个域名，区分优先级进行回源，优先级1为最高，当优先级为1 的域名不能访问时自动访问优先级为2的域名，以此类推。

**oss回源**

![image.png](https://img1.jcloudcs.com/cms/25340540-9284-4691-80b9-3135e01d339020180118102645.png)

- 当回源方式选择“OSS域名”时，回源地址以下拉列表的方式展示所有OSS域名信息（从对象存储服务同步）供客户单选。

**回源host**

指的是CDN节点回源过程中所需访问的服务器域名。

例如回源host是www.a.com，CDN节点在回源时请求到www.a.com解析后对应的服务器

 ![image.png](https://img1.jcloudcs.com/cms/35c3ff38-b7a9-45c3-8509-c323488936f520180118102722.png)

**源站监控**

开启源站监控后，CDN分发节点将按照探测周期探测源站的可用性及网络延迟情况，您可以到【管理】-【云监控】配置并查询源站的异常告警信息。

![image.png](https://img1.jcloudcs.com/cms/ce478878-87ee-49a0-a29b-f72e6b61606f20180118102744.png)

-  “监控链接”配置内容为：（二选一）

- 标准监控链接：在客户加速域名根目录下放入特定的文件，如：www.jdcloud.com/monitor.gif
- 自定义监控链接:文本框输入，由客户自定义监测文件及监测文件路径

- 探测周期：分为一分钟和五分钟
- Headers：指探测方身份校验信息，以key-value形式客户自定义

探测内容包括：

 ![image.png](https://img1.jcloudcs.com/cms/92dced92-dc84-4027-8f4c-351a0063743820180118101549.png)

 