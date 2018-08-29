# CVE-2017-8464:Microsoft Windows LNK远程代码执行漏洞

2017年6月13日，微软官方发布编号为CVE-2017-8464的漏洞公告，官方介绍Windows系统在解析快捷方式时存在远程执行任意代码的高危漏洞，黑客可以通过U盘、网络共享等途径触发漏洞，完全控制用户系统，安全风险高危。

具体详情如下:

漏洞编号:

CVE-2017-8464

漏洞名称:

Microsoft Windows LNK 远程代码执行漏洞

官方评级:

高危

漏洞描述:

攻击者可以向用户呈现包含恶意的.LNK文件和相关联的恶意二进制文件的可移动驱动器或远程共享。 当用户在Windows资源管理器或解析.LNK文件的任何其他应用程序中打开此驱动器（或远程共享）时，恶意二进制程序将在目标系统上执行攻击者选择的代码，成功利用此漏洞的攻击者可以获得与本地用户相同的用户权限。

注释:.LNK是windows系统内应用程序快捷方式文件的文件类型后缀名。

漏洞利用条件和方式:

远程利用

漏洞影响范围:

1.桌面系统

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

2.服务器系统

* Microsoft Windows Server 2008 R2 for Itanium-based Systems SP1
* Microsoft Windows Server 2008 R2 for x64-based Systems SP1
* Microsoft Windows Server 2008 for 32-bit Systems SP2
* Microsoft Windows Server 2008 for Itanium-based Systems SP2
* Microsoft Windows Server 2008 for x64-based Systems SP2
* Microsoft Windows Server 2012
* Microsoft Windows Server 2012 R2
* Microsoft Windows Server 2016

漏洞检测:

无

漏洞修复建议(或缓解措施):

* 不要使用管理员权限运行程序，为应用程序新建普通账号并授权，最小化权限运行应用程序
* 尽快升级安装微软补丁，京东云用户可以通过windows系统自动升级功能和手工下载安装，补丁下载链接:[https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2017-8464](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2017-8464)

情报来源:

* [https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2017-8464](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2017-8464)
* [http://www.securityfocus.com/bid/98818](http://www.securityfocus.com/bid/98818)