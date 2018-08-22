# Windows2008计算机管理找不到磁盘管理的处理方法
**问题现象：**

Windows 2008服务器在计算机管理的存储里面，查看不到磁盘管理，无法对磁盘做管理。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%AE%A1%E7%90%86%E6%89%BE%E4%B8%8D%E5%88%B0%E7%A3%81%E7%9B%98%E7%AE%A1%E7%90%86%E7%9A%84%E5%A4%84%E7%90%86%E6%96%B9%E6%B3%9501.png)

**问题原因：**

一般都是系统组策略中的磁盘管理服务被禁用导致的

**解决办法：**

1.点击开始-运行-输入*gpedit.msc*，打开组策略。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%AE%A1%E7%90%86%E6%89%BE%E4%B8%8D%E5%88%B0%E7%A3%81%E7%9B%98%E7%AE%A1%E7%90%86%E7%9A%84%E5%A4%84%E7%90%86%E6%96%B9%E6%B3%9502.png)

2.依次点击【本地计算机策略】→【用户配置】→【管理模板】→【Windows组件】→【Microsoft 管理控制台】→【受限的/许可的管理单元】→双击【磁盘管理】。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%AE%A1%E7%90%86%E6%89%BE%E4%B8%8D%E5%88%B0%E7%A3%81%E7%9B%98%E7%AE%A1%E7%90%86%E7%9A%84%E5%A4%84%E7%90%86%E6%96%B9%E6%B3%9503.png)

3.点击【未配置】→【确定】。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%AE%A1%E7%90%86%E6%89%BE%E4%B8%8D%E5%88%B0%E7%A3%81%E7%9B%98%E7%AE%A1%E7%90%86%E7%9A%84%E5%A4%84%E7%90%86%E6%96%B9%E6%B3%9504.png)

4.打开命令提示符，执行*gpupdate*更新组策略。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%AE%A1%E7%90%86%E6%89%BE%E4%B8%8D%E5%88%B0%E7%A3%81%E7%9B%98%E7%AE%A1%E7%90%86%E7%9A%84%E5%A4%84%E7%90%86%E6%96%B9%E6%B3%9505.png)

如无法解决您的问题，请向我们提工单。
