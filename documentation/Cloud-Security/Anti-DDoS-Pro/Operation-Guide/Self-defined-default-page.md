# 自定义返回页面

当触发DDoS IP高防CC自定义防护封禁，或者DDoS IP高防节点返回异常状态码（590/592/594）时，即返回相应的默认页面。同时也支持用户自定义页面，并应用到实例下的所有域名或CC自定义防护规则。

应用场景举例：重视自身品牌露出的客户，例如游戏或电商行业客户，在源站业务不可用的情况下，要求客户端访问页面返回的是客户品牌logo页或广告页面，而不是安全产品的默认页面，自定义返回页面能满足客户此类需求。

## 操作步骤
1. 登录 [DDoS IP高防 控制台](https://ip-anti-console.jdcloud.com/instancelist)。
2. 在 **实例列表** 页面，选择目标实例，点击 **实例名称** 或 **转发配置**，进入 **实例详情** 页面。
3. 在 **实例详情** 页面，点击 **自定义返回页面** 编辑按钮。</br>
![](../../../../image/Advanced%20Anti-DDoS/self-define%20default%20page01.png)</br>
4. 在 **自定义页面** 中，点击 **添加** 可创建自定义页面，一个实例下支持最多创建3个自定义页面。</br>
![](../../../../image/Advanced%20Anti-DDoS/self-define%20default%20page02.png)</br>
5. 输入页面名称，并以标准html格式输入页面内容，支持最多不超过10000个字符的内容。</br>
![](../../../../image/Advanced%20Anti-DDoS/self-define%20default%20page03.png)</br>
6. 编辑完成后，审核状态默认为 **审核中** ，等待京东云安全管理人员后台人工审核通过，审核状态修改为 **审核通过** 后，即可在实例和CC自定义规则下引用该页面。</br>
![](../../../../image/Advanced%20Anti-DDoS/self-define%20default%20page05.png)</br>
7. 返回 **实例详情** 页面，下拉列表选择自定义页面，即可在该实例下生效，此时DDoS IP高防节点返回的异常状态码页面即为自定义页面。</br>
![](../../../../image/Advanced%20Anti-DDoS/self-define%20default%20page04.png)</br>
8. 自定义页面支持在CC定义防护规则中引用，进入CC防护自定义规则页面，阻断类型选择 **封禁** ，即可在 **封禁并返回自定义页面** 中引用自定义页面。</br>
![](../../../../image/Advanced%20Anti-DDoS/self-define%20default%20page06.png)</br>
