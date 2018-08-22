# IIS7.5开启500真实报错
Windows 云主机使用 IIS 作为 Web 服务的网站，访问时出现“500 - 内部服务器错误”如下图所示。此报错并没有输出具体的错误项，给排查问题带来一些困难，可以通过以下方法显示程序的真实报错，以便针对性分析网站错误。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/iis7.5%E5%BC%80%E5%90%AF500%E7%9C%9F%E5%AE%9E%E6%8A%A5%E9%94%9901.png)

**具体步骤如下：**

1.远程连接云主机，在菜单栏，选择 开始 > 管理工具 > Internet Information Service(IIS)管理器。

2.在左侧导航窗格单击 网站，找到报错站点，找到并打开 错误页 文件，如下图所示。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/iis7.5%E5%BC%80%E5%90%AF500%E7%9C%9F%E5%AE%9E%E6%8A%A5%E9%94%9902.png)

3.在右侧的 操作 栏里，单击 编辑功能设置。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/iis7.5%E5%BC%80%E5%90%AF500%E7%9C%9F%E5%AE%9E%E6%8A%A5%E9%94%9903.png)

4.在弹出的 编辑错误页设置 窗口中，选择 详细错误 后，单击 确定。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/iis7.5%E5%BC%80%E5%90%AF500%E7%9C%9F%E5%AE%9E%E6%8A%A5%E9%94%9904.png)

如无法解决您的问题，请向我们提工单。
