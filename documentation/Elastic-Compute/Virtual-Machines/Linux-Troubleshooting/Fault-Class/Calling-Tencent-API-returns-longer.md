# 调用腾讯API返回时长较长

在程序中调用腾讯等其他第三方API接口时，会出现返回时间较长的问题，该问题的原因是访问API接口的URL时，在DNS解析上消耗了较长时间，需要手动添加第三方API接口网站的域名解析，或者修改DNS配置，优先使用公共DNS服务器。举例如下：

编写go语言程序调用腾讯地图API，输出调用返回的时间。在未添加域名解析或修改DNS服务器配置时，调用返回时间是10秒左右，如图：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/%E8%B0%83%E7%94%A8%E8%85%BE%E8%AE%AFAPI%E8%BF%94%E5%9B%9E%E6%97%B6%E9%95%BF%E8%BE%83%E9%95%BF01.png)

可通过修改DNS服务器优先级配置优化调用返回时间，方法如下：

*vi /etc/resolv.conf* 可以看到公用DNS服务器8.8.8.8的优先级最低，如图：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/%E8%B0%83%E7%94%A8%E8%85%BE%E8%AE%AFAPI%E8%BF%94%E5%9B%9E%E6%97%B6%E9%95%BF%E8%BE%83%E9%95%BF02.png)

编辑该文件，将公共DNS服务器8.8.8.8条目写至最前，即把8.8.8.8服务器的优先级调至最高，如图：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/%E8%B0%83%E7%94%A8%E8%85%BE%E8%AE%AFAPI%E8%BF%94%E5%9B%9E%E6%97%B6%E9%95%BF%E8%BE%83%E9%95%BF03.png)

wq退出编辑并保存文件，再次执行测试程序，调用返回时间降至300ms左右，如图：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/%E8%B0%83%E7%94%A8%E8%85%BE%E8%AE%AFAPI%E8%BF%94%E5%9B%9E%E6%97%B6%E9%95%BF%E8%BE%83%E9%95%BF04.png)

另外一种方法是修改/etc/hosts文件，在文件中添加调用API网站的域名解析，如图：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/%E8%B0%83%E7%94%A8%E8%85%BE%E8%AE%AFAPI%E8%BF%94%E5%9B%9E%E6%97%B6%E9%95%BF%E8%BE%83%E9%95%BF05.png)

保存文件后再次运行测试程序，调用返回时间进一步降至80ms左右，如图：

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/%E8%B0%83%E7%94%A8%E8%85%BE%E8%AE%AFAPI%E8%BF%94%E5%9B%9E%E6%97%B6%E9%95%BF%E8%BE%83%E9%95%BF06.png)

使用该方法可以省去到公共DNS服务器进行域名解析的时间，但是存在两个缺点：

1、如果需要调用的API网站较多，需要逐一手动添加

2、添加的解析是静态解析，只是访问网站的几个IP中的一个，如果解析的IP地址因某些原因无法访问，会返回公共DNS服务器进行解析，如果不修改解析IP，仍会出现调用时间较长的问题

综上所述，修改DNS服务器优先级或者添加本地解析这两种方法请根据自身情况选择使用。
