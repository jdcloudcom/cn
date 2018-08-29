# CVE-2017-8543:Microsoft Windows Search远程命令执行漏洞

2017年6月13日，微软官方在例行补丁日发布编号为CVE-2017-8543的漏洞公告，当Windows搜索处理内存中的对象时，存在远程执行代码漏洞。成功利用此漏洞的攻击者可以控制受影响的系统。

具体详情如下:

漏洞编号:

CVE-2017-8543

漏洞名称:

Windows Search远程代码执行漏洞

官方评级:

高危

漏洞描述:

Windows搜索服务（WSS）是windows的一项默认启用的基本服务。攻击者可以向Windows Search服务发送精心构造的SMB消息，从而利用此漏洞提升权限并控制计算机。

漏洞利用条件和方式:

远程利用

漏洞影响范围:

桌面系统

* Microsoft Windows 10 Version 1607 for 32-bit Systems
* Microsoft Windows 10 Version 1607 for x64-based Systems
* Microsoft Windows 10 for 32-bit Systems
* Microsoft Windows 10 for x64-based Systems
* Microsoft Windows 10 version 1511 for 32-bit Systems
* Microsoft Windows 10 version 1511 for x64-based Systems
* Microsoft Windows 10 version 1703 for 32-bit Systems
* Microsoft Windows 10 version 1703 for x64-based Systems
* Microsoft Windows 7 for 32-bit Systems SP1
* Microsoft Windows 7 for x64-based Systems SP1
* Microsoft Windows 8.1 for 32-bit Systems
* Microsoft Windows 8.1 for x64-based Systems
* Microsoft Windows RT 8.1

服务器系统

* Microsoft Windows Server 2008 R2 for Itanium-based Systems SP1
* Microsoft Windows Server 2008 R2 for x64-based Systems SP1
* Microsoft Windows Server 2008 for 32-bit Systems SP2
* Microsoft Windows Server 2008 for Itanium-based Systems SP2
* Microsoft Windows Server 2008 for x64-based Systems SP2
* Microsoft Windows Server 2012
* Microsoft Windows Server 2012 R2
* Microsoft Windows Server 2016
* Microsoft Windows Server 2003

漏洞检测:

无

漏洞修复建议(或缓解措施):

* 不要使用管理员权限运行程序，为应用程序新建普通账号并授权，最小化权限运行应用程序
* 尽快升级安装微软补丁，京东云用户可以通过windows系统自动升级功能和手工下载安装，补丁下载链接:[https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2017-8543](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2017-8543)

情报来源:

* [https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2017-8543](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2017-8543)
* [http://www.securityfocus.com/bid/98824](http://www.securityfocus.com/bid/98824)