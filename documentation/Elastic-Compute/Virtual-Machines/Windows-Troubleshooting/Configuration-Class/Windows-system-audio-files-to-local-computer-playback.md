# Windows系统音频文件转本地电脑播放
**问题现象：**

windows系统远程连接后，右下角的声音显示红叉，无法播放远程声音；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E9%9F%B3%E9%A2%91%E6%96%87%E4%BB%B6%E8%BD%AC%E6%9C%AC%E5%9C%B0%E7%94%B5%E8%84%91%E6%92%AD%E6%94%BE01.png)

**处理方法：**

可以通过设置本地电脑远程桌面工具的方法，将远程的声音在本地电脑上播放；
云主机内请先调整下如下设置；

**windows 2008系统：**

1 远程连接后，点击开始-管理工具-远程桌面服务-远程桌面会话主机；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E9%9F%B3%E9%A2%91%E6%96%87%E4%BB%B6%E8%BD%AC%E6%9C%AC%E5%9C%B0%E7%94%B5%E8%84%91%E6%92%AD%E6%94%BE02.png)

2 双击rdp-tcp，选择客户端设置，将音频和视频播放的勾选取消；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E9%9F%B3%E9%A2%91%E6%96%87%E4%BB%B6%E8%BD%AC%E6%9C%AC%E5%9C%B0%E7%94%B5%E8%84%91%E6%92%AD%E6%94%BE03.png)

3 点击开始-运行-输入*services.msc*，找到“Windows Audio”服务，将此服务设置为自动，并启动下，之后将此次的远程连接关闭；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E9%9F%B3%E9%A2%91%E6%96%87%E4%BB%B6%E8%BD%AC%E6%9C%AC%E5%9C%B0%E7%94%B5%E8%84%91%E6%92%AD%E6%94%BE04.png)


**windows 2012系统：**

1 打开windows powershell，输入*gpedit.msc*，打开组策略；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E9%9F%B3%E9%A2%91%E6%96%87%E4%BB%B6%E8%BD%AC%E6%9C%AC%E5%9C%B0%E7%94%B5%E8%84%91%E6%92%AD%E6%94%BE05.png)

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E9%9F%B3%E9%A2%91%E6%96%87%E4%BB%B6%E8%BD%AC%E6%9C%AC%E5%9C%B0%E7%94%B5%E8%84%91%E6%92%AD%E6%94%BE06.png)

2 依次点击“计算机配置”-“管理模版”-“windows 组件”-“远程桌面服务”-“远程桌面会话主机”-“设备和资源重定向”，打开“允许音频和视频播放重定向”，选择“已启用”;

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E9%9F%B3%E9%A2%91%E6%96%87%E4%BB%B6%E8%BD%AC%E6%9C%AC%E5%9C%B0%E7%94%B5%E8%84%91%E6%92%AD%E6%94%BE07.png)

3 继续在windows powershell中输入*services.msc*打开服务，找到“Windows Audio”服务，将此服务设置为自动，并启动下，之后将此次的远程连接关闭；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E9%9F%B3%E9%A2%91%E6%96%87%E4%BB%B6%E8%BD%AC%E6%9C%AC%E5%9C%B0%E7%94%B5%E8%84%91%E6%92%AD%E6%94%BE08.png)

以上配置调整完成后，打开本地远程桌面软件进行配置。

**本地电脑Windows xp系统：**

打开本地远程桌面软件，点击 选项 - 本地资源，选择远程计算机声音的下拉菜单，选择 带到这台计算机。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E9%9F%B3%E9%A2%91%E6%96%87%E4%BB%B6%E8%BD%AC%E6%9C%AC%E5%9C%B0%E7%94%B5%E8%84%91%E6%92%AD%E6%94%BE09.png)

**本地电脑Windows 7系统：**

打开本地远程桌面软件，点击“选项”-“本地资源”，在远程声音处点击“设置”，弹出的选项卡中的远程音频播放处，选择“在此计算机中播放”，点击确定；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E9%9F%B3%E9%A2%91%E6%96%87%E4%BB%B6%E8%BD%AC%E6%9C%AC%E5%9C%B0%E7%94%B5%E8%84%91%E6%92%AD%E6%94%BE10.png)

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E9%9F%B3%E9%A2%91%E6%96%87%E4%BB%B6%E8%BD%AC%E6%9C%AC%E5%9C%B0%E7%94%B5%E8%84%91%E6%92%AD%E6%94%BE11.png)

再次连接后，可以看到右下角声音处显示已经正常，此时在远程打开音频文件，本地是可以正常听到声音的；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E9%9F%B3%E9%A2%91%E6%96%87%E4%BB%B6%E8%BD%AC%E6%9C%AC%E5%9C%B0%E7%94%B5%E8%84%91%E6%92%AD%E6%94%BE12.png)

如无法解决您的问题，请向我们提工单。
