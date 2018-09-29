# URL白名单配置
以下将介绍网站类防护规则的一些常见配置。</BR>
规则配置前，需要定位到网站转发规则处，步骤如下：
- 首先需要登录 [IP高防 控制台](https://ip-anti-console.jdcloud.com/instancelist)。
- 找到需要配置的实例，单击实例名称，进入 **实例详情** 页面。
- 切换到 **网站转发配置** 
   ![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/web-rule%2002.png)



### 操作步骤
1. 单击 **防护规则** ，展开防护规则配置。
 ![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/web-rule%2004.png)
2. 单击URL白名单旁的 **编辑** 按钮，在如下弹窗中进行白名单编辑
 ![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/web-rule%2005.png)
3. 编辑完成后开启URL白名单的按钮，则规则生效。</BR>
 ![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/web-rule%2006.png)
 
 配置说明：
-  网站类规则，支持配置50条URL白名单，策略默认关闭。
- URL白名单，支持泛域名 * 的配置，不支持正则表达式和通配符配置。




