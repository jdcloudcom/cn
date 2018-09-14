# Windows2012 ie浏览器打不开
**问题现象：**

打开ie浏览器，提示如下错误：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%20ie%E6%B5%8F%E8%A7%88%E5%99%A8%E6%89%93%E4%B8%8D%E5%BC%8001.png)

**解决办法：**

1.右键开始，选择运行。在弹出的窗口中输入 *secpol.msc* 命令。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%20ie%E6%B5%8F%E8%A7%88%E5%99%A8%E6%89%93%E4%B8%8D%E5%BC%8002.png)

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%20ie%E6%B5%8F%E8%A7%88%E5%99%A8%E6%89%93%E4%B8%8D%E5%BC%8003png)

2.在弹出的页面中，点击选择“安全设置-本地策略-安全选项”菜单，在依次展开的页面中进行对应的设置。在打开的安全选项右侧页面中，点击找到“用户账户控制：用于内置管理员账户的管理员批准模式”选项。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%20ie%E6%B5%8F%E8%A7%88%E5%99%A8%E6%89%93%E4%B8%8D%E5%BC%8004.png)

3.双击打开页面设置之后，我们点击将该选项设置为"已启用"按钮，然后点击确定按钮保存对账户安全策略的设置。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%20ie%E6%B5%8F%E8%A7%88%E5%99%A8%E6%89%93%E4%B8%8D%E5%BC%8005.png)

4.重启服务器生效。



如无法解决您的问题，请向我们提工单。
