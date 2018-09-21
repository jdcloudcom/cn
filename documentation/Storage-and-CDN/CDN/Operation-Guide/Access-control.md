
# 访问控制

**Referer防盗链**

通过配置访问的referer黑白名单来对访问者身份进行识别和过滤，从而限制资源被访问的情况。

![image.png](https://img1.jcloudcs.com/cms/cae838c5-ec36-405a-8d72-a1dfe1ff517120180403184257.png)

- referer黑名单：不允许符合规则的请求来访问；referer白名单：允许符合规则的请求来访问
- 允许通过浏览器直接访问资源URL：是否允许无referer字段的请求访问（目前只支持无referer字段，referer字段为空的场景后续支持）
- referer黑白名单配置只能生效一种，选择白名单时，不能规则和“允许通过浏览器直接范文资源URL”均为空
- 支持多个referer配置，最多50个，且不能重复
- 支持泛域名规则配置

**IP黑名单**

禁止来自黑名单的IP访问该域名

**![image.png](https://img1.jcloudcs.com/cms/cb6511da-4608-4c31-b628-d9be43546cc120180403191802.png)**

- 可设置多个IP以及IP地址段，最多添加50个
- 不能重复添加同一个IP

 


