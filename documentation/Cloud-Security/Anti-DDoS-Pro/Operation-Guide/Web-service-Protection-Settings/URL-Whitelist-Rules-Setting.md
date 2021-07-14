# 黑白名单配置
黑白名单允许您设置访问控制规则，对常见的HTTP字段（如IP、URI、Headers、Cookie）进行条件组合，用来筛选访问请求，并对命中条件的请求设置放行、阻断等匹配动作。</BR>
配置前，需要定位到网站转发规则处，步骤如下：
- 首先需要登录 [DDoS IP高防 控制台](https://ip-anti-console.jdcloud.com/instancelist)。
- 找到需要配置的实例，单击实例名称，进入 **实例详情** 页面。
- 切换到 **网站转发配置** 
   ![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/web-rule%2009.png)



### 操作步骤
1. 单击 **防护规则** ，进入网站类防护规则界面。
 ![网站防护规则](../../../../../image/Advanced%20Anti-DDoS/web-service-rule-01.png)
2. 单击黑/白名单的 **去设置** 按钮，在如下页面中添加编辑黑/白名单。
 ![网站黑白名单](../../../../../image/Advanced%20Anti-DDoS/web-service-rule-02.png)
3. 单击 **添加** ，添加黑/白名单规则，设置规则的匹配条件和相应的匹配动作。</BR>
 ![网站黑白名单](../../../../../image/Advanced%20Anti-DDoS/web-service-rule-03.png)
4. 编辑完成后开启黑/白名单的状态按钮，则规则生效。</BR>
 ![网站黑白名单](../../../../../image/Advanced%20Anti-DDoS/web-service-rule-04.png)

配置说明
 -  黑/白名单分别可以配置10条。</BR>
 -  匹配规则包括：URI、IP、Cookie、Geo、headers。</BR>
 -  当匹配规则为URI时，匹配值填写以/开头的URI路径。</BR>
 -  当匹配规则为IP时，匹配值指定引用的IP黑白名单规则。</BR>
 -  当匹配规则为Cookie时，填写Key值和匹配值。</BR>
 -  当匹配规则为Geo时，匹配值选择区域。</BR>
 -  当匹配规则为headers时，Key值可选择Date/Host/Referer等字段或切换为手动输入。</BR>
 -  匹配模式：完全匹配、前缀匹配、后缀匹配、正则匹配、包含。</BR>
 -  白名单匹配动作：包含放行和CC防护。默认选择放行，匹配白名单的流量不做过滤，全部放行；选择CC防护时，则对匹配白名单的流量进行CC防护。</BR>
 -  黑名单匹配动作：包含阻断，跳转到其他页面，验证码。选择阻断后可选择自定义返回页面。选择跳转到其他页面需指定页面的URI。</BR>
 -  规则开关默认打开，关闭时该规则不生效。</BR>




