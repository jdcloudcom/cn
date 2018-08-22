# Windows修改DNS的方法

**问题描述：**

Windows系统如何修改DNS。

**解决方案：**

Windows系统服务器，DNS默认是自动获取的，如果用户想使用自己配置的DNS或者公网的dDNS进行解析，可以参考如下方法修改下服务器的DNS：

1. 打开网络和共享中心；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E4%BF%AE%E6%94%B9DNS%E7%9A%84%E6%96%B9%E6%B3%9501.png)

2.选择"更改适配器设置"；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E4%BF%AE%E6%94%B9DNS%E7%9A%84%E6%96%B9%E6%B3%9502.png)

3.选择网卡，右击选择“属性”；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E4%BF%AE%E6%94%B9DNS%E7%9A%84%E6%96%B9%E6%B3%9503.png)

4.双击“Intrtnet 协议版本4（TCP/IPV4）”，在出现的选项卡下方向输入要使用的DNS地址就可以，可以使用公网114.114.114.114 和 114.114.115.115这组DNS，或者改为其他您想使用公网DNS。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E4%BF%AE%E6%94%B9DNS%E7%9A%84%E6%96%B9%E6%B3%9504.png)

