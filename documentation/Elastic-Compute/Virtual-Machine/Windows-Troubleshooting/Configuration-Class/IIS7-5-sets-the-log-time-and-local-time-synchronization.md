# IIS7.5设置日志时间和本地时间同步

**问题现象：**

IIS服务中的web日志和ftp日志记录的时间点和服务器系统时间不一致，相差8小时，如图：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/iis7.5%E8%AE%BE%E7%BD%AE%E6%97%A5%E5%BF%97%E6%97%B6%E9%97%B4%E5%92%8C%E6%9C%AC%E5%9C%B0%E6%97%B6%E9%97%B4%E5%90%8C%E6%AD%A501.png)

**问题原因：**

由于IIS日志的机制，IIS日志W3C格式是以格林尼治时间创建的，因此和服务器系统时间要差8个小时。


**解决办法：**

打开IIS管理器，点击ftp站点，右侧点击ftp日志。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/iis7.5%E8%AE%BE%E7%BD%AE%E6%97%A5%E5%BF%97%E6%97%B6%E9%97%B4%E5%92%8C%E6%9C%AC%E5%9C%B0%E6%97%B6%E9%97%B4%E5%90%8C%E6%AD%A502.png)

将最下面的使用本地时间进行文件命名和滚动更新选项前面打钩，点击应用即可。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/iis7.5%E8%AE%BE%E7%BD%AE%E6%97%A5%E5%BF%97%E6%97%B6%E9%97%B4%E5%92%8C%E6%9C%AC%E5%9C%B0%E6%97%B6%E9%97%B4%E5%90%8C%E6%AD%A503.png)

如无法解决您的问题，请向我们提工单。
