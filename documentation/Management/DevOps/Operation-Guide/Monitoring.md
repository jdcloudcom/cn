# 智能监控

**前言**

智能监控是一套覆盖基础监控，存活监控，性能监控和业务监控的全链路监控系统。通过监控您可以全面了解资源的使用情况，性能和运行状态。通过异常检测和多维度数据分析可及时对止损做出反应，缩短异常MTTR，保障业务正常运行。


**术语定义**

- NS：namespace的缩写，代表监控对象，可以是一个机器、一个实例、一个域名、一个应用、一个系统。
- 监控对象类型：基本的监控对象类型分为host（机器）、instance（实例），当做了聚合计算- 后，监控对象类型分为app（应用）、system（系统）。
- 基础监控：基础监控项是指机器的监控项，常见的有cpu.idle、mem.free.percent等。
- 端口监控：监控端口的状态、响应时间。
- 进程监控：监控进程的状态、占用资源。
- 日志监控：从日志当中监控关键字、PV等。
- 自定义监控：通过用户的脚本进行自定义监控。
- 报警ACK：指确认报警，并正在处理。系统会记录下ACK报警的人员信息。
- 报警修复：对于因配置变更，无法回到恢复状态的报警事件，手动将其状态改为恢复。
- 报警屏蔽：针对NS或报警配置，屏蔽报警事件的邮件、短信和语音，但事件会被记录在报警历史中。

**产品功能**

**监控配置**

1.采集配置。除了基础监控项不需要配采集配置，其他类型的监控都需要配置采集配置，支持的监控类型包括进程监控、端口监控、日志监控和自定义监控。

![image](https://github.com/jdcloudcom/cn/blob/DevOps/image/DevOps/Operation-Guide17.png)
 
2.聚合配置。聚合配置分一次聚合与二次聚合。一次聚合是在应用节点范围内计算聚合值；二次聚合是在一次聚合的前提上，在系统范围内计算聚合值，并且可以对这些聚合值做四则运算。

3.报警配置。报警配置中可以为监控项配置报警规则、报警联系人组和报警方式。

 ![image](https://github.com/jdcloudcom/cn/blob/DevOps/image/DevOps/Operation-Guide18.png)

4.创建好服务树后，默认会根据服务树中的角色，创建系统运维、系统测试和应用研发报警组。

 ![image](https://github.com/jdcloudcom/cn/blob/DevOps/image/DevOps/Operation-Guide19.png)

5.每个产品线、每个系统节点都可以创建一个值班组，方便值班人员轮询接收报警。

 ![image](https://github.com/jdcloudcom/cn/blob/DevOps/image/DevOps/Operation-Guide20.png)

**报警管理**

1.报警历史。报警历史中可以查看触发报警规则的所有事件，有统计面板和列表，支持报警历史分享和下载功能。

 ![image](https://github.com/jdcloudcom/cn/blob/DevOps/image/DevOps/Operation-Guide21.png)

2.报警屏蔽。对于已知故障和处理中的故障，可设置屏蔽，在屏蔽时间段内不会收到报警，避免干扰，屏蔽时间到后自动开启报警。支持按报警规则和单个，多个ns屏蔽报警。

 ![image](https://github.com/jdcloudcom/cn/blob/DevOps/image/DevOps/Operation-Guide22.png)

**数据可视化**

1.仪表盘。可以将日常需要看的图表配置在仪表盘中，随时都可以查看。并且仪表盘支持阈值筛选，即仅显示满足阈值条件的监控项数据，可以更加快捷地发现异常和故障。目前仪表盘支持趋势图和列表两种组件。

 ![image](https://github.com/jdcloudcom/cn/blob/DevOps/image/DevOps/Operation-Guide23.png)

2.趋势图。在趋势图上方勾选NS和监控指标，就能查看趋势图数据，支持统计值的切换、单位的切换，并支持分享，大图等功能。

 ![image](https://github.com/jdcloudcom/cn/blob/DevOps/image/DevOps/Operation-Guide24.png)

3.单IP搜图。当仅想查看某一个IP的监控项时，或者要查询的IP不在权限范围内的服务树上，可以通过单IP搜图查到这个IP的监控数据。但仅限机器和实例的监控指标。

![image](https://github.com/jdcloudcom/cn/blob/DevOps/image/DevOps/Operation-Guide25.png)
