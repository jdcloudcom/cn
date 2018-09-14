# Windows远程登录提示没有登录的权限
**问题现象：**

Windows远程登录提示“要登录到这台远程计算机，您必须被授予允许通过终端服务登录的权限。默认地，"远程桌面用户"组的成员拥有该权限。如果您不是"远程桌面用户"组或其它拥有该权限的组的成员，或者如 果"远程桌面用户"组没有该权限，您必须手动授予这些权限。”如下图：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%BF%9C%E7%A8%8B%E7%99%BB%E5%BD%95%E6%8F%90%E7%A4%BA%E6%B2%A1%E6%9C%89%E7%99%BB%E5%BD%95%E7%9A%84%E6%9D%83%E9%99%9001.png)

**问题原因：**

组策略配置中对允许登录终端的用户或者组做了限制；

 

**解决办法：**

1.点击开始-运行，输入*gpedit.msc*，打开“本地组策略编辑器”；

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%BF%9C%E7%A8%8B%E7%99%BB%E5%BD%95%E6%8F%90%E7%A4%BA%E6%B2%A1%E6%9C%89%E7%99%BB%E5%BD%95%E7%9A%84%E6%9D%83%E9%99%9002.png)


2.在“本地组策略编辑器”中点击“计算机配置”-->“Windows设置”-->“安全设置”-->“本地策略”--> “用户权限分配”。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%BF%9C%E7%A8%8B%E7%99%BB%E5%BD%95%E6%8F%90%E7%A4%BA%E6%B2%A1%E6%9C%89%E7%99%BB%E5%BD%95%E7%9A%84%E6%9D%83%E9%99%9003.png)

3.右侧找到“拒绝通过远程桌面服务登录”打开，查看有无需要登录的帐号，如有请删除下。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%BF%9C%E7%A8%8B%E7%99%BB%E5%BD%95%E6%8F%90%E7%A4%BA%E6%B2%A1%E6%9C%89%E7%99%BB%E5%BD%95%E7%9A%84%E6%9D%83%E9%99%9004.png)


4.之后在看下"允许通过远程桌面服务登录"，查看有无需要登录的用户帐号，如没有添加下对应的账户。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%BF%9C%E7%A8%8B%E7%99%BB%E5%BD%95%E6%8F%90%E7%A4%BA%E6%B2%A1%E6%9C%89%E7%99%BB%E5%BD%95%E7%9A%84%E6%9D%83%E9%99%9005.png)

5.之后测试登录云主机正常。
