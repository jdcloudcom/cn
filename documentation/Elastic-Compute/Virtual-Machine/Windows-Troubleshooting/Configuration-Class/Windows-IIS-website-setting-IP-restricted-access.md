# Windows IIS网站设置IP限制访问
使用Windows IIS搭建的网站如遇到恶意IP攻击，会导致网站服务出现异常，此时可以使用IIS的安全模块中的IP限制功能禁止恶意IP访问网站。配置步骤如下：

1、在服务器管理器面板仪表板页面点击右上角的工具菜单（红框处），选择IIS管理器，启动IIS管理界面

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%20IIS%E7%BD%91%E7%AB%99%E8%AE%BE%E7%BD%AEIP%E9%99%90%E5%88%B6%E8%AE%BF%E9%97%AE01.png)

2、在左侧边栏逐级选择想要配置的网站，修改红框中的分组依据为类别，在安全性中选择“IP地址和域限制”

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%20IIS%E7%BD%91%E7%AB%99%E8%AE%BE%E7%BD%AEIP%E9%99%90%E5%88%B6%E8%AE%BF%E9%97%AE02.png)

注意“IP地址和域限制”功能需要在安装IIS组件时勾选上，如果没有勾选，则无法使用该功能。如果在安全性类别中没有找到该项图标，说明系统上没有安装该组件，请按如下步骤安装：

1）点击任务栏左侧红框处启动服务器管理器面板，再点击仪表板中的添加角色和功能（蓝框处），启动添加角色和功能向导

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%20IIS%E7%BD%91%E7%AB%99%E8%AE%BE%E7%BD%AEIP%E9%99%90%E5%88%B6%E8%AE%BF%E9%97%AE03.png)

2）点击下一步，直到服务器角色步骤，逐级选择Web服务器（IIS）-->Web服务器 -->安全性，勾选“IP地址和域限制”，点击下一步直至确认页面，然后点击安装。确认安装完成后，关闭添加角色和功能向导即可。此时重启IIS管理器，在网站功能页面中就会显示“IP地址和域限制”图标。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%20IIS%E7%BD%91%E7%AB%99%E8%AE%BE%E7%BD%AEIP%E9%99%90%E5%88%B6%E8%AE%BF%E9%97%AE04.png)

3、在“IP地址和域限制”页面，点击右侧操作栏中的添加拒绝条目，编辑拒绝的IP地址

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%20IIS%E7%BD%91%E7%AB%99%E8%AE%BE%E7%BD%AEIP%E9%99%90%E5%88%B6%E8%AE%BF%E9%97%AE05.png)

4、如针对单独IP进行访问拒绝，勾选特定IP地址，在空白栏中输入IP地址后点击确定即可

5、如针对IP段进行访问拒绝，勾选IP地址范围，在第一个空白栏输入IP段固定部分，变化部分用0替代，如图所示，在第二个空白栏中输入掩码，用于指定IP段的范围。输入完毕后点击确定即可

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%20IIS%E7%BD%91%E7%AB%99%E8%AE%BE%E7%BD%AEIP%E9%99%90%E5%88%B6%E8%AE%BF%E9%97%AE06.png)

6、成功添加条目后，在“IP地址和域限制”页面可以看到条目内容，注意条目内容添加后无法修改，只能删除条目，选中条目后点击右侧操作栏中的删除即可。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%20IIS%E7%BD%91%E7%AB%99%E8%AE%BE%E7%BD%AEIP%E9%99%90%E5%88%B6%E8%AE%BF%E9%97%AE07.png)
