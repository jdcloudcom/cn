# Windows2008安装配置ftp服务
注意：本文相关 Windows 配置及说明已在 Windows2008 64位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。

**安装**

1.选择左下角的服务器管理器。点击角色，添加角色。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A101.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A102.png)

2.默认下一步，在选择服务器角色中，勾选Web服务器（IIS）。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A103.png)

3.默认下一步，在选择角色服务中，勾选FTP服务器。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A104.png)

4.默认下一步，点击安装，直到完成。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A105.png)

**配置**

1.服务器管理器，点击左侧栏的角色，Web服务器（IIS），Internet信息服务（IIS）管理器。右键中间栏的主机名选项，选择添加FTP站点。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A106.png)

2.设置FTP站点名称，和FTP内容目录物理路径。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A107.png)

3.设置FTP服务端口为默认的21端口，ssl勾选无。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A108.png)

4.身份验证选择基本，指定用户，填写ftp账户名称，赋予读取和写入权限。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A109.png)

5.服务器管理器，配置，本地用户和组，右键用户，选择新用户。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A110.png)

6.设置ftp用户名和密码。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A111.png)

7.右键ftp内容目录，选择属性。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A112.png)

8.选择安全，编辑。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A113.png)

9.选择添加。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A114.png)

10.选择高级，立即查找，找到ftp账户，选择确定。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A115.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A116.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A117.png)

11.赋予ftp账户读取和写入权限。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A118.png)

**防火墙配置**

1.左下角开始，控制面板。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A119.png)

2.双击windows防火墙，选择高级设置。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A120.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A121.png)

3.左侧栏选择入站规则，右侧栏选择新建规则。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A122.png)

4.选择端口，本地特定端口，填写21。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A123.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A124.png)

5.选择允许连接，填写名称，完成。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A125.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A126.png)


至此ftp服务和防火墙配置完成。

如无法解决您的问题，请向我们提工单。
