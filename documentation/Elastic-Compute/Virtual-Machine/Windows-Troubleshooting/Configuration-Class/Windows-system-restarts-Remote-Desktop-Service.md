# Windows系统重启远程桌面服务
Windows系统服务器默认远程登陆的3389端口暴露在公网，如果经常被暴力破解，即使不能成功入侵也会造成远程桌面服务异常；


建议修改远程桌面端口，也可以通过控制台终端登陆服务器重启远程桌面服务（Remote Desktop Services）的方式处理；


进入云主机控制台，点击页面的远程连接进入系统；


依次点击-开始-管理工具-服务，找到Remote Desktop Services右键点击重新启动即可；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E9%87%8D%E5%90%AF%E8%BF%9C%E7%A8%8B%E6%A1%8C%E9%9D%A2%E6%9C%8D%E5%8A%A101.png)

重启后通过远程桌面测试登陆已经恢复；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E9%87%8D%E5%90%AF%E8%BF%9C%E7%A8%8B%E6%A1%8C%E9%9D%A2%E6%9C%8D%E5%8A%A102.png)
