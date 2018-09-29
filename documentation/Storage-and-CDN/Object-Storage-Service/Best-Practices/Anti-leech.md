# 防盗链最佳实践

为了防止存储在对象存储中的数据被其他人盗链，京东云对象存储支持基于HTTP Header Referer字段的防盗链方法。可通过控制台设置Referer字段的白名单。设置白名单后，只有Referer字段在白名单内的用户才可访问Bucket中存储的数据，不在白名单内的请求会被拒绝。但若未配置Referer白名单时，默认可访问，不受白名单限制。

## 防盗链

A网站将自己的静态资源如图片或视频等存放在京东云存储的OSS上。B网站在未经A允许的情况下，使用A网站的图片或视频资源，放置到自己的网站中。这样网站B盗取了网站A的空间和流量，而A没有获取任何利益却承担了资源使用费。B盗用A资源放到自己网站的行为即为盗链。

防盗链的主要方法是通过设置Referer防盗链限制引用页来实现的：

设置Referer防盗链的原理将HTTP请求表头的Referer属性（保存了该请求是从哪个URL发送到服务器的）和服务端许可的白名单进行比对，如果一致则表明是站内请求，或者为自己信任的站点请求；若不一致，则视为盗链，并拒绝该站的请求。

## Referer

Referer是HTTP请求表头的一个参数，不同场景下HTTP请求表头的Referer属性会有差异：

直接访问服务器端资源：即浏览器直接请求OSS的资源，则HTTP请求中不包含Referer属性

在网站A中引用OSS的资源：浏览器访问的是网站http://jd.com/ 页面，该页面上引用了OSS的资源。浏览器向OSS请求资源时，HTTP的请求头中包含了Referer属性，该属性指明是http://jd.com/ 页面引用了该资源。

## 配置防盗链

1.进入京东云对象存储页面，进入某一Bucket下空间设置-权限设置页面，如下图所示：

![权限设置](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-075.jpg)

2.将该Bucket的读写权限设置为自定义权限后，点击添加自定义权限，如下图所示：

![自定义权限](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-076.jpg)

3.勾选“设置”Referer白名单，即可设置Referer白名单及设置是否允许Referer为空。

4.配置Referer的更多详细操作请访问访问权限设置。


下面将介绍不同设置对应的不同结果：

假设源站为http://jd.com/ ，盗链网站为http://jd-steal.com/

a.设置Referer白名单，且不允许referer为空，能实现防盗链功能

![白名单](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-077.jpg)

访问结果如下：

|访问类型|说明|结果|
|-|-|-|
|http://test-refer.oss.cn-east-1.jcloudcs.com/example.jpg |直接访问，Referer为空|不允许Referer为空的请求，返回403|
|http://jd.com/|请求来自于与源站|访问成功|
|http://jd-steal.com/|请求来自于盗链网站|返回403|

b.设置Referer白名单，且允许referer为空，能实现防盗链功能

![白名单](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-078.jpg)

访问结果如下：

|访问类型|说明|结果|
|-|-|-|
|http://test-refer.oss.cn-east-1.jcloudcs.com/example.jpg |直接访问，Referer为空|允许Referer为空的请求，访问成功|
|http://jd.com/ |请求来自于与源站|访问成功|
|http://jd-steal.com/ |请求来自于盗链网站|返回403|
c.设置Referer白名单为空，若HTTP请求中若带有Referer，OSS将拒绝所有网站发起的请求，包括信任网站，所以不推荐使用该配置。若您需要实现防盗链功能，请使用前两种配置方案。
