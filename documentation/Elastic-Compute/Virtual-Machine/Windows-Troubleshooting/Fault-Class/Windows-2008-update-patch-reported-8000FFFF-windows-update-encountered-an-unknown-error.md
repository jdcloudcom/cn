# Windows2008 更新补丁报“8000FFFFwindows update 遇到未知错误”
**问题现象：**

Windows2008 R2 更新补丁报“代码 8000FFFF windows update 遇到未知错误“：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20%E6%9B%B4%E6%96%B0%E8%A1%A5%E4%B8%81%E6%8A%A5%E2%80%9C8000FFFFwindows%20update%20%E9%81%87%E5%88%B0%E6%9C%AA%E7%9F%A5%E9%94%99%E8%AF%AF%E2%80%9D01.png)

**问题原因：**

该问题主要原因是因为 C 盘无 user 权限，导致更新的补丁无法正常安装。

**解决办法：**

为C盘加上user权限，只需要给读写权限即可，为了系统安全在补丁更新完成以后去掉user权限，避免留下安全隐患。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20%E6%9B%B4%E6%96%B0%E8%A1%A5%E4%B8%81%E6%8A%A5%E2%80%9C8000FFFFwindows%20update%20%E9%81%87%E5%88%B0%E6%9C%AA%E7%9F%A5%E9%94%99%E8%AF%AF%E2%80%9D02.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20%E6%9B%B4%E6%96%B0%E8%A1%A5%E4%B8%81%E6%8A%A5%E2%80%9C8000FFFFwindows%20update%20%E9%81%87%E5%88%B0%E6%9C%AA%E7%9F%A5%E9%94%99%E8%AF%AF%E2%80%9D03.png)

如果以上方法还是无法解决，参考以下方法，通常可以解决：

1.停止自动更新 和 BITS服务。在命令提示符中执行：

***net stop wuauservnet stop bits***

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20%E6%9B%B4%E6%96%B0%E8%A1%A5%E4%B8%81%E6%8A%A5%E2%80%9C8000FFFFwindows%20update%20%E9%81%87%E5%88%B0%E6%9C%AA%E7%9F%A5%E9%94%99%E8%AF%AF%E2%80%9D04.png)

2.删除系统中 “C:\Windows\SoftwareDistribution” 文件夹。



3.启动自动更新服务和 BITS服务，当这两个服务运行后会自动创建“C:\Windows\SoftwareDistribution”文件夹。在命令提示符中执行：

***net start wuauservnet start bits***

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20%E6%9B%B4%E6%96%B0%E8%A1%A5%E4%B8%81%E6%8A%A5%E2%80%9C8000FFFFwindows%20update%20%E9%81%87%E5%88%B0%E6%9C%AA%E7%9F%A5%E9%94%99%E8%AF%AF%E2%80%9D05.png)

4.停止 Cryptographic服务。在命令提示符中执行：

***net stop cryptsvc***

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20%E6%9B%B4%E6%96%B0%E8%A1%A5%E4%B8%81%E6%8A%A5%E2%80%9C8000FFFFwindows%20update%20%E9%81%87%E5%88%B0%E6%9C%AA%E7%9F%A5%E9%94%99%E8%AF%AF%E2%80%9D06.png)

5.重命名 C:\windows\System32\catroot2文件夹为：C:\windows\System32\catroot2.bak。

6.C:\Windows\SoftwareDistribution” 文件夹生成后, 做自动更新检测，在命令提示符中执行：

***wuauclt.exe /resetauthorization /detectnow***

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%20%E6%9B%B4%E6%96%B0%E8%A1%A5%E4%B8%81%E6%8A%A5%E2%80%9C8000FFFFwindows%20update%20%E9%81%87%E5%88%B0%E6%9C%AA%E7%9F%A5%E9%94%99%E8%AF%AF%E2%80%9D07.png)

7.15分钟后查看系统是否检测到更新，如果检测到，通常就可以正常安装。

如无法解决您的问题，请向我们提工单。
