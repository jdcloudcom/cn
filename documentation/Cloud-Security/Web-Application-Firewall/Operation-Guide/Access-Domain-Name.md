## **接入域名**

请到DNS服务商处添加CNAME记录，使web应用防火墙防护生效。

以京东云云解析为例：

1、首先复制云WAF界面中的生成的防护域名。

![TimLine图片20180515200411.png](http://img1.jcloudcs.com/cms/ab31748e-9fda-4fab-95a9-7de6dd39685f20180515200512.png)

2、添加一条京东云云解析CNAME记录，主机记录填写您的现有域名如下图的aaa，将刚才WAF界面中生成的防护域名填入到记录值一栏中(如下图的ddd.bbb.com)，其余选项填写默认即可。（若未添加域名需先添加主域名）

![TimLine图片20180515201408.png](http://img1.jcloudcs.com/cms/d94e8a0a-5f36-4f8c-9c3c-44ade00f93fb20180515201413.png)