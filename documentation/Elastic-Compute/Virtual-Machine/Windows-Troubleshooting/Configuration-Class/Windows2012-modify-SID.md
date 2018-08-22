# Windows2012修改SID
SID也就是安全标识符（Security Identifiers），是标识用户、组和计算机帐户的唯一的号码。在云上安装AD和我们线下安装AD步骤其实一样，但客户端加入域的步骤稍有不同，需要先修改客户端的SID，这是因为云服务器系统采用的同一个镜像，所以SID是相同的，如果不修改，在加入域的时候会提示SID相同，因此我们需要修改服务器的SID，修改前建议您参考：《制作私有镜像》创建一个私有镜像，一旦修改失败造成系统异常，可以通过镜像恢复系统。修改操作会重启服务器系统，并且重新进入设置页面，建议您通过控制台终端登陆操作；

首先，*cd C:\Windows\System32\Sysprep*进入Sysprep目录，然后执行sysprep就可以打开系统准备工具，勾选“通用”后点击确定：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E4%BF%AE%E6%94%B9SID01.png)

提示Sysprep正在工作：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E4%BF%AE%E6%94%B9SID02.png)

重新进入设置页面：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E4%BF%AE%E6%94%B9SID03.png)

点击下一步>接受，之后重新输入密码：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E4%BF%AE%E6%94%B9SID04.png)

按照提示操作，重新登陆到系统中。
输入*whoami /user*查看SID已经做了修改：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2012%E4%BF%AE%E6%94%B9SID05.png)
