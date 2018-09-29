# 云物理服务器常见问题

1. Q:单用户云物理服务器配额？
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A:单个用户无配额，但是单笔订单最大支持订购5台。

2. Q:有公网和内网IP吗？
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A:基础网络环境下每个云物理服务器提供一个公网IP和一个内网IP。用户可选择10/192/172开头的内网CIDR网段。IP地址由系统自动分配，用户不可指定。

3. Q:不同地域之间内网互通吗？不同可用区之间内网互通吗？
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A:不同地域之间内网不互通，不同可用区之间内网不互通。

4. Q:用户可以创建多少个内网？
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A:用户在同一可用区只能创建一个内网，且只能在创建第一台云物理服务器的时候设置内网CIDR段。用户在该可用区创建第二台及以上的云物理服务器的时候，会沿用第一次创建的内网网段。

5. Q:云物理服务器的操作系统密码忘记了怎么办？
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A:目前重置密码需要用户手工提交工单，线下处理。

6. Q:云物理服务器如何保证高可用性？
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A:京东云对云物理服务器在网络架构上保证高可用性。业务层的高可用性架构需要用户自己设计。

7. Q:云物理服务器的安全防护性能如何？
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A:云物理服务器自带免费2G的DDoS基础防护，并对初始化安装的OS进行防火墙设置（外网只允许IN22端口）。

8. Q:云物理服务器是否支持Linux内核升级？
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A:京东云对云物理服务器对升级Linux内核并未设限，但不建议用户进行内核升级操作。因为京东云仅为官方提供的版本负责，如果升级后出现任何使用问题均需要用户自己承担后果。

9. Q:我的云物理服务器遇到问题需要找谁咨询和处理？
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A:当您的云物理服务器遇到问题，可以通过在线客服、4006151212电话等形式，联系我们的客服人员处理。

10. Q:控制台支持的浏览器有哪些？
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A:
&nbsp;- 优先推荐chrome：31.0.1650.57以上。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 其他浏览器的支持程度正在测试中。

11. Q:云物理服务器是否支持运行虚拟化软件服务应用？
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A:云物理服务器是您独享的物理服务器，支持虚拟化的部署和开发。

12.Q:云物理服务器是否可以更改网卡配置？
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A:云物理服务器不支持更改网卡配置，否则会导致网络异常无法正常使用。

13.Q:云物理服务器的系统盘是否支持分区操作？
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A:云物理服务器的系统盘不建议强行分区，否则会导致系统无法正常使用。

14.Q:云物理服务器是否可以安装第三方软件？
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A:京东云物理服务器默认不限制客户安装第三方软件，但是用户需要自行维护所租用的物理服务器的安全。如果服务器因为用户的原因遭到攻击，可能会被京东云的安全部门进行警告甚至断网操作。
