# Windows2012安装配置ftp服务
注意：本文相关 Windows 配置及说明已在 Windows2012 64位操作系统中进行过测试。其它类型及版本操作系统配置可能有所差异，具体情况请参阅相应操作系统官方文档。

**安装**

1.选择左下角的服务器管理器。点击管理，添加角色和功能。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A101.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A102.png)

2.默认下一步，在选择服务器角色中，勾选Web服务器（IIS），选择添加功能，下一步。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A103.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A104.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A105.png)

3.默认下一步，在选择角色服务中，勾选FTP服务器，FTP服务，选择下一步进行安装。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A106.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A107.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A108.png)

**配置**

1.服务器管理器，选择工具，Internet Information Services（IIS）管理器。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A109.png)

2.左侧栏右键网站，选择添加FTP站点。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A110.png)

3.设置ftp站点名称和ftp内容目录物理路径。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A111.png)

4.设置ftp默认端口为21，选择无SSL。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A112.png)

5.身份验证选择基本，允许访问设置为指定用户，填写ftp用户名，添加读取和写入权限。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A113.png)

6.服务器管理器，选择工具，计算机管理。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A114.png)

7.本地用户和组，右键用户，选择新用户。创建ftp用户，设置密码。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A115.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A116.png)

8.右键ftp内容目录，选择属性。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A117.png)

9.选择安全，编辑，添加。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A118.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A119.png)

10.选择高级，立即查找，选择ftp用户。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A120.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A121.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A122.png)

11.给ftp用户添加读取和写入权限。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A123.png)

**防火墙配置**

1.左下角开始，打开控制面板。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A124.png)

2.选择windows防火墙，高级设置。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A125.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A126.png)

3.左侧选择入站规则，右侧选择新建规则。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A127.png)

4.选择端口，输入ftp服务的默认端口21，选择允许连接，输入规则名称，完成。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A128.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A129.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A130.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A131.png)

5.控制面板，windows防火墙，允许应用或者功能通过Windows防火墙。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A132.png)

6.选择允许其他应用，浏览。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A133.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A134.png)

7.找到"C:\Windows\System32\svchost.exe"，双击选择添加。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A135.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E5%AE%89%E8%A3%85%E9%85%8D%E7%BD%AEftp%E6%9C%8D%E5%8A%A136.png)

至此ftp服务和防火墙配置完成。



如无法解决您的问题，请向我们提工单。

