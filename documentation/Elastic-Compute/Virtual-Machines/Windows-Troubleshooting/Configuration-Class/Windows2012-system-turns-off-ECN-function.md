# Windows2012系统关闭ECN功能
远程桌面登陆服务器后点击Windows Power Shell，输入*netsh  int  tcp  show  global*，查看ECN功能状态：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E7%B3%BB%E7%BB%9F%E5%85%B3%E9%97%ADECN%E5%8A%9F%E8%83%BD01.png)

输入*netsh int tcp set global ecn=disable*后回车，正常返回确定消息，再次输入*netsh  int  tcp  show  global*查看，ECN功能被正常关闭。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E7%B3%BB%E7%BB%9F%E5%85%B3%E9%97%ADECN%E5%8A%9F%E8%83%BD02.png)

如无法解决您的问题，请向我们提工单。
