# 查看安全报表
DDoS IP高防提供丰富的安全报表，帮助您了解接入高防后的防护效果。

## 操作步骤
### 方法1
登录DDoS IP高防 [监控报表页面](https://ip-anti-console.jdcloud.com/charts)。默认将显示第一个实例的相关报表。您可以在 **实例名称** 的下拉框中进行实例切换，也可以选择多个或全部实例。若选择多个实例，则报表中图的数据将累加显示。
![图表](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/report%2006.png)

### 方法2
登录 [DDoS IP高防控制台](https://ip-anti-console.jdcloud.com/instancelist)。找到想查看报表的实例，点击**查看报表**，即可查看该实例的报表。</br>
![图表](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/report%2009.png)

## 报表类型
DDoS IP高防的报表分为四类，DDoS攻击防护、业务流量、CC防护和连接数。默认展示当天的报表，可选择7天、30天。最大可查看30天内的报表情况，报表粒度最小为5分钟。报表下方是攻击日志的显示。</BR>

1. DDoS攻击防护报表</BR>
包括防护前的流量和防护后的流量对比。单击图表上方图例，可隐藏防护前或防护后的流量曲线。拖动图表下方时间窗口滚动条，可在当前查询时间范围内缩小时间窗口查询。鼠标移到到图上可展示该线条的流量数据。</BR>
![图表](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/report%2010.png)

2. 业务流量报表</BR>
包括IN和OUT两个方向的流量，IN流量是经过清洗后，转发到源站服务器的流量，OUT流量是源站服务器的响应流量。</BR>
![图表](../../../../image/Advanced%20Anti-DDoS/report%2011.png)

3. CC防护报表</BR>
DDoS IP高防防御的CC攻击，会生成CC防护报表，CC报表支持切换不同的域名,CC防护仅对网站类业务有效。</BR>
![图表](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/report%2012.png)

4. 连接数报表</BR>
新建连接数：系统在1秒内建立的连接数。</BR>
![图表](../../../../image/Advanced%20Anti-DDoS/report%2013.png)


