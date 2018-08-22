# Windows云主机调整激活方式为KMS

京东云云主机从2018年6月起陆续完成了各地域官方Windows Server镜像的微软正版激活方式调整，从原来的MAK激活更改为KMS激活，KMS激活为内网激活，不需要云主机连接公网或手动电话激活，便于内网服务器的初始激活。

1、登录云主机 **开始－>运行－>键入cmd** 进入MS-DOS命令模式

2、查看当前激活方式

***slmgr /dlv

3、如为MAK激活请先卸载MAK产品密钥

***slmgr /upk

4、清除注册表信息

***slmgr /cpky

5、安装KMS激活的产品密钥

***slmgr /ipk "KMS-Client-Setup-Key

"KMS-Client-Setup-Key"为各操作系统版本对应的统一KMS激活密钥，如下：

操作系统及版本	                                                   KMS客户端激活密钥

Windows Server 2016 数据中心版 64位 中文版	
CB7KF-BWN84-R7R2Y-793K2-8XDDG
Windows Server 2012 R2 标准版 64位 中文版	
D2N9P-3P6X9-2R39C-7RTCD-MDVJX
Windows Server 2008 R2 数据中心版 64位 中文版	
74YFP-3QFB3-KQT8W-PMXWJ-7M648

（如您使用的Windows Server镜像为已下线的早期镜像，可以前往Microsoft官网查找对应激活密钥：https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj612867(v%3dws.11)）

6、 设置激活服务器地址

*slmgr /skms 169.254.169.250:1688*

7、重置授权状态

*Slmgr /rearm*

8、重启云主机

9、激活云主机

*slmgr /ato*

10、再次查看确认是否成功调整为KMS激活

*slmgr /dlv*

关于MAK和KMS激活资料可参考：

（MAK激活介绍：https://technet.microsoft.com/en-us/library/ff793435.aspx）

（KMS激活介绍：https://technet.microsoft.com/en-us/library/ff793434.aspx）
