# Windows关闭ie浏览器增强安全性
由于为了服务器操作系统的安全性，当在Windows Sever2008 & 2012 中运行IE的时候会发现默认情况下IE启用了增强的安全配置，导致访问网站会提示如下信息：
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/windows%E5%85%B3%E9%97%ADie%E6%B5%8F%E8%A7%88%E5%99%A8%E5%A2%9E%E5%BC%BA%E5%AE%89%E5%85%A8%E6%80%A701.png)

如果需要访问时不提示此信息，需要关闭ie增强安全性功能。

**Windows2008系统进行如下操作：**

1.点击左下角服务器管理器。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/windows%E5%85%B3%E9%97%ADie%E6%B5%8F%E8%A7%88%E5%99%A8%E5%A2%9E%E5%BC%BA%E5%AE%89%E5%85%A8%E6%80%A702.png)

2.左侧列表栏选择服务器管理器，右侧列表栏选择配置 IE ESC。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/windows%E5%85%B3%E9%97%ADie%E6%B5%8F%E8%A7%88%E5%99%A8%E5%A2%9E%E5%BC%BA%E5%AE%89%E5%85%A8%E6%80%A703.png)

3.将ie增强的安全配置，管理员和用户项都调整为禁用。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/windows%E5%85%B3%E9%97%ADie%E6%B5%8F%E8%A7%88%E5%99%A8%E5%A2%9E%E5%BC%BA%E5%AE%89%E5%85%A8%E6%80%A704.png)

设置完毕后，重启ie 浏览器，访问网站就不会有安全提示了。

**Windows2012系统进行如下操作：**

1.点击左下角服务器管理器。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/windows%E5%85%B3%E9%97%ADie%E6%B5%8F%E8%A7%88%E5%99%A8%E5%A2%9E%E5%BC%BA%E5%AE%89%E5%85%A8%E6%80%A705.png)

2.左侧列表栏选择本地服务器，右侧列表栏选择IE 增强的安全配置，选择启用选项。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/windows%E5%85%B3%E9%97%ADie%E6%B5%8F%E8%A7%88%E5%99%A8%E5%A2%9E%E5%BC%BA%E5%AE%89%E5%85%A8%E6%80%A706.png)

3.将ie增强的安全配置，管理员和用户项都调整为关闭。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/windows%E5%85%B3%E9%97%ADie%E6%B5%8F%E8%A7%88%E5%99%A8%E5%A2%9E%E5%BC%BA%E5%AE%89%E5%85%A8%E6%80%A707.png)

设置完毕后，重启ie 浏览器，访问网站就不会有安全提示了。

如无法解决您的问题，请向我们提工单。
