# Windows带宽占用高的处理
**导致服务器出带宽占用高的可能原因：**

1.客户正常应用业务访问频繁，正常占用较高带宽。

2.恶意病毒、木马引起的网络流量。有时三方恶意程序可能会利用操作系统的svchost.exe，或者 Tcpsvcs.exe来伪装，引起高带宽的占用。

3.Windows自身服务(更新服务等)可能会占用较高网络流量。

**通过windows资源监视器查看占用出带宽的进程：**

Windows 2008 R2，打开任务管理器 -> 性能 -> 资源监视器 -> 网络， 如下图：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E5%B8%A6%E5%AE%BD%E5%8D%A0%E7%94%A8%E9%AB%98%E7%9A%84%E5%A4%84%E7%90%8601.png)

Windows 2012 R2，打开任务管理器 -> 性能 -> 资源监视器 -> 网络， 如下图：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E5%B8%A6%E5%AE%BD%E5%8D%A0%E7%94%A8%E9%AB%98%E7%9A%84%E5%A4%84%E7%90%8602.png)

如果该进程是正常业务进程，确实因为客户端访问量大造成带宽占用高，请酌情考虑购买更多带宽。

如果该进程是名称可疑进程，请尝试直接杀死进程，或者使用专业杀毒软件进行杀毒后观察服务器行为。

如无法解决您的问题，请向我们提工单。
