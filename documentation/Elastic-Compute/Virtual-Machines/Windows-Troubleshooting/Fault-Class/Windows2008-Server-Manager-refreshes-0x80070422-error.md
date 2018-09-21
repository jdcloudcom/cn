# Windows2008服务器管理器刷新报0x80070422错误 
**问题现象：**

windows服务器管理器刷新失败，提示如下错误：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E6%9C%8D%E5%8A%A1%E5%99%A8%E7%AE%A1%E7%90%86%E5%99%A8%E5%88%B7%E6%96%B0%E6%8A%A50x80070422%E9%94%99%E8%AF%AF01.png)

**问题原因：**

Windows Modules Installer服务器没有开启导致。



**解决方法：**

登录服务器桌面左下脚点击”开始”->”运行”，输入services.msc打开服务；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E6%9C%8D%E5%8A%A1%E5%99%A8%E7%AE%A1%E7%90%86%E5%99%A8%E5%88%B7%E6%96%B0%E6%8A%A50x80070422%E9%94%99%E8%AF%AF02.png)

找到Windows Modules Installer服务右键点击选择启动；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E6%9C%8D%E5%8A%A1%E5%99%A8%E7%AE%A1%E7%90%86%E5%99%A8%E5%88%B7%E6%96%B0%E6%8A%A50x80070422%E9%94%99%E8%AF%AF03.png)

之后再次打开服务器管理器便正常了。



如无法解决您的问题，请向我们提工单。
