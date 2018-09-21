# 查看安全报表
IP高防提供丰富的安全报表，帮助您了解接入高防后的防护效果。

## 操作步骤
### 方法1
1. 登录IP高防 [监控报表页面](https://ip-anti-console.jdcloud.com/charts)。菜单栏位置如下：</BR>
![](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/report%2001.png)
2. 默认将显示第一个实例的相关报表。您可以在**实例名称**的下拉框中进行实例切换，也可以选择多个或全部实例。若选择多个实例，则报表中图的数据将累加显示。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/report%2006.png)
### 方法2
1. 登录 [IP高防控制台](https://ip-anti-console.jdcloud.com/instancelist)。
2. 找到想查看报表的实例，点击**查看报表**，即可查看该实例的报表。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/report%2002.png)

## 报表类型
IP高防的报表分为三类，DDoS攻击防护、转发流量和CC防护。默认展示当天的报表，可选择7天、30天。最大可查看30天内的报表情况，报表粒度最小为5分钟。报表下发是攻击日志的显示。
1. DDoS攻击防护报表</BR>
包括防护前的流量和防护后的流量对比。单击图例，可只查看防护前或防护后的流量。鼠标移到到图上可展示该线条的流量数据。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/report%2003.png)
2. 转发流量报表</BR>
从IP高防转发回源站的流量，可在转发流量报表里查看。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/report%2004.png)
3. CC防护报表</BR>
IP高防防御的CC攻击，会生成CC防护报表，CC报表支持切换不同的域名。</BR>
因为CC防护仅对网站类生效，所有CC防护报表中，只能展示网站类转发规则产生的CC防护流量。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/report%2005.png)


