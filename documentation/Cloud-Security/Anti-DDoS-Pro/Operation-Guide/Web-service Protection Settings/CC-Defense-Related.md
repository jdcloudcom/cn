# CC防护规则相关配置
CC防护规则属于网站类防护的规则，需要先切换网站类转发配置。</BR>
步骤如下：
- 首先需要登录 [IP高防 控制台](https://ip-anti-console.jdcloud.com/instancelist)。
- 找到需要配置的实例，单击实例名称，进入 **实例详情** 页面。
- 切换到 **网站转发配置** 
   ![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/web-rule%2002.png)
   
### 操作步骤
1. 单击 **防护规则** ，展开防护规则配置。
 ![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/web-rule%2004.png)
2. 配置全局CC防护策略。
 ![网站转发规则](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/CC%20rules%2001.png)
以下是规则解释：
- 防护规则里的CC防护针对全局生效，如果开启则全局CC防护开启。
- 如果关闭全局CC防护，则网站转发配置中所有已配置的域名，其CC防护也将全部关闭。
- CC防护峰值，显示的是所购买套餐中的CC防护峰值大小。
- CC防护模式配置。系统支持四种CC防护模式的选择：</BR>
“宽松”：仅很少部分的访问会经过CC规则校验，适用于较少访问的网站。</BR>
“正常”：网站无明显异常时，请选用正常模式。仅对部分访问进行校验检查</BR>
“紧急”：网站响应缓慢，CPU、内存等出现异常时，请使用紧急模式。该模式检查严格，可能存在误伤。</BR>
“自定义”：适用于高级用户，可自定义防护阈值。包括HTTP请求数阈值，每个Host的防护阈值，每个Host+URI的防护阈值，每个源IP对Host的防护阈值，每个源IP对Host+URI的防护阈值。最大HTTP请求数阈值，不超过购买套餐的阈值。</BR>

3. 配置单个域名的CC防护策略。</BR>
 - 若全局CC防护已开启，可关闭某个单独的域名的CC防护。
 - 若全局CC防护已关闭，则不支持打开单个域名CC防护。
4. CC观察模式</BR>
若CC观察模式开启，则CC防护只告警，不防御。
5.  配置限速
- 高防支持对源IP访问速率的限制。单击限速规则中的“编辑”按钮，设置即可。最小时间支持设置到秒。


