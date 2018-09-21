# Windows2008 iis服务配置https
**创建证书：**

1、使用Windows  Server 2008 R2的CA服务来创建证书，通过“服务器管理器”中的“添加角色”。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps01.png)

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps02.png)

2、选择“Active Directory 证书服务”。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps03.png)

3、添加服务的时候需要选择：“证书颁发机构”“证书颁发机构Web注册”“联机响应程序”三个服务。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps04.png)

4、因为不是域控环境，所以选择“独立（A）”即可。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps05.png)

5、安装的第一个CA，选择“根CA（R)”即可。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps06.png)

6、选择“新建私钥（R）”即可。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps07.png)

7、这里保持默认即可，当然如果需要自定义的设置，也可以自行选择。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps08.png)

8、此处的CA名称，建议保持默认即可。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps09.png)

9、设置证书的时间，默认是5年，这个可以根据Web的情况，自行设置。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps10.png)

10、设置证书数据库位置和日志位置，自行选择即可。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps11.png)

**创建IIS服务：**

1、安装好CA证书后，安装程序会自动引导开始IIS的安装。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps12.png)

2、这个里需要勾选“ASPNETt”和“.NET 扩展性”。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps13.png)

3、需要说明的是，安装了证书后，不能更改计算机名或域名。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps14.png)

4、最后，确保证书服务和Web服务器IIS是安装成功的。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps15.png)

**创建自签名证书：**

1、在IIS管理器中选择“服务器证书”。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps16.png)

2、选中先前创建好的证书，然后选择“创建自签名证书”。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps17.png)

3、设置一个简明知意的名称。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps18.png)

**搭建https网站：**

1、新添加一个网站。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps19.png)

2、设置好网站的主目录，设置类型为https，SSL证书选择前期设置好的testca即可。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps20.png)

3、在网站根目录中设置一个Index.html的测试页面。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps21.png)

4、选择站点，点击默认文档。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps22.png)

5、把Index.html默认文档上移到顶部。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps23.png)

6、在外网使用HTTPS的方式做访问测试，可以看到可以访问，不过因为证书不是公共CA机构颁发的，所以会有安全提示，如果购买了CA证书，使用付费的证书，通常就不会有这个安全风险提示。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps24.png)

7、选择“继续前往”可以看到网站能够正常访问。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20iis%E6%9C%8D%E5%8A%A1%E9%85%8D%E7%BD%AEhttps25.png)

如无法解决您的问题，请向我们提工单。
