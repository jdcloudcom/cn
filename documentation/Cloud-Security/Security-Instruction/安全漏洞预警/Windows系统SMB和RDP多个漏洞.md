尊敬的京东云用户:

2017年4月14日，国外黑客组织Shadow Brokers发出了NSA方程式组织的机密文档，包含了多个Windows远程漏洞利用工具，该工具包可以可以覆盖全球70%的Windows服务器，可以导致服务器被入侵，为了确保您在京东云上的业务安全，请您关注:

一.影响范围：

已知受影响的Windows版本包括但不限于：

Windows NT、Windows 2000、Windows XP、Windows 2003、Windows Vista、Windows 7、Windows 8，Windows 2008、Windows 2008 R2、Windows Server 2012 SP0；

二.排查方式

本次曝出的工具利用SMB服务和RDP服务远程入侵，需要确认服务器是否对外开启了137、139、445、3389端口。

排查方式如下:

外网计算机上telnet目标地址445，例如：telnet【IP】445

三.缓解措施

1.微软已经发出[通告](https://blogs.technet.microsoft.com/msrc/2017/04/14/protecting-customers-and-evaluating-risk/?from=timeline&isappinstalled=0)，强烈建议您更新最新补丁；

******工具名称**
 
******解决措施** “EternalBlue”
 
Addressed by [MS17-010](https://technet.microsoft.com/en-us/library/security/ms17-010.aspx) “EmeraldThread”
 
Addressed by [MS10-061](https://technet.microsoft.com/en-us/library/security/ms10-061.aspx) “EternalChampion”
 
Addressed by [CVE-2017-0146](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2017-0146) & [CVE-2017-0147](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2017-0147) “ErraticGopher”
 
Addressed prior to the release of Windows Vista “EsikmoRoll”
 
Addressed by [MS14-068](https://technet.microsoft.com/en-us/library/security/ms14-068.aspx) “EternalRomance”
 
Addressed by [MS17-010](https://technet.microsoft.com/en-us/library/security/ms17-010.aspx) “EducatedScholar”
 
Addressed by [MS09-050](https://technet.microsoft.com/en-us/library/security/ms09-050.aspx) “EternalSynergy”
 
Addressed by [MS17-010](https://technet.microsoft.com/en-us/library/security/ms17-010.aspx) “EclipsedWing”
 
Addressed by [MS08-067](https://technet.microsoft.com/en-us/library/security/ms08-067.aspx)

2.如果您业务上没有使用137、139、445端口，您可以使用安全组或者防火墙添加公网入策略：屏蔽137、139、445端口；

3.使用安全组或者防火墙添加公网入策略：限制3389远程登录源IP地址。

我们将持续关注该事件的后续进展，有最新消息，我们将第一时间同步，感谢您对京东云的支持！