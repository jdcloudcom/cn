# Windows文件属性没有安全选项卡
**问题现象：**

Windows服务器鼠标右键点击文件或者文件夹属性的时候，没有安全选项卡，导致无法修改文件或者文件夹的权限，现象如图：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E6%96%87%E4%BB%B6%E5%B1%9E%E6%80%A7%E6%B2%A1%E6%9C%89%E5%AE%89%E5%85%A8%E9%80%89%E9%A1%B9%E5%8D%A101.png)

**解决办法：**

1.点击开始-运行-输入*gpedit.msc*打开组策略。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E6%96%87%E4%BB%B6%E5%B1%9E%E6%80%A7%E6%B2%A1%E6%9C%89%E5%AE%89%E5%85%A8%E9%80%89%E9%A1%B9%E5%8D%A102.png)

2.点击用户配置-管理模版-Windows组件-Windows资源管理器-右侧找到"删除"安全"选项卡"。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E6%96%87%E4%BB%B6%E5%B1%9E%E6%80%A7%E6%B2%A1%E6%9C%89%E5%AE%89%E5%85%A8%E9%80%89%E9%A1%B9%E5%8D%A103.png)

3.双击打开"删除"安全"选项卡"，改为"未配置"，点击确定即可。之后右键点击文件或者文件夹便可以看到安全选项卡了。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E6%96%87%E4%BB%B6%E5%B1%9E%E6%80%A7%E6%B2%A1%E6%9C%89%E5%AE%89%E5%85%A8%E9%80%89%E9%A1%B9%E5%8D%A104.png)

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E6%96%87%E4%BB%B6%E5%B1%9E%E6%80%A7%E6%B2%A1%E6%9C%89%E5%AE%89%E5%85%A8%E9%80%89%E9%A1%B9%E5%8D%A105.png)

如无法解决您的问题，请向我们提工单。
