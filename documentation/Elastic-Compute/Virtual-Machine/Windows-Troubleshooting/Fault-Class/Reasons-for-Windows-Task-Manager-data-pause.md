# Windows任务管理器数据暂停的原因
**问题现象：**

在查看任务管理时，“进程”选项卡的 CPU、内存数据没有刷新，或发现性能选项卡的数据没有变动或一直处于0但实际上服务器是有网络传输的。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E4%BB%BB%E5%8A%A1%E7%AE%A1%E7%90%86%E5%99%A8%E6%95%B0%E6%8D%AE%E6%9A%82%E5%81%9C%E7%9A%84%E5%8E%9F%E5%9B%A001.png)

**问题原因：**

任务管理器更新速度已暂停导致的。

**解决办法：**

点击“查看”->更新速度，检查是否被配置为“已暂停”，可以将它改为“普通或正常”，然后观察一下任务管理器中的数据是否正常刷新了。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E4%BB%BB%E5%8A%A1%E7%AE%A1%E7%90%86%E5%99%A8%E6%95%B0%E6%8D%AE%E6%9A%82%E5%81%9C%E7%9A%84%E5%8E%9F%E5%9B%A002.png)

如无法解决您的问题，请向我们提工单。
