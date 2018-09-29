# Windows远程提示出现身份验证错误，要求的函数不受支持
**问题现象：**

远程桌面连接显示：发生身份验证错误 要求的函数不受支持。如图：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%BF%9C%E7%A8%8B%E6%8F%90%E7%A4%BA%E5%87%BA%E7%8E%B0%E8%BA%AB%E4%BB%BD%E9%AA%8C%E8%AF%81%E9%94%99%E8%AF%AF%EF%BC%8C%E8%A6%81%E6%B1%82%E7%9A%84%E5%87%BD%E6%95%B0%E4%B8%8D%E5%8F%97%E6%94%AF%E6%8C%8101.png)

**问题原因：**

2018年5月8日，微软发布的更新补丁，将windows的默认设置，从“易受攻击”修改为“缓解”。这个更新补丁要求服务器端和客户端都更新后，才可以实现远程连接。当云主机未更新该补丁，但是用户客户端更新补丁时，就会出现无法远程连接服务器的情况。



**解决方法：**

1.客户端在运行中输入*gpedit.msc*，进入本地组策略编辑器。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%BF%9C%E7%A8%8B%E6%8F%90%E7%A4%BA%E5%87%BA%E7%8E%B0%E8%BA%AB%E4%BB%BD%E9%AA%8C%E8%AF%81%E9%94%99%E8%AF%AF%EF%BC%8C%E8%A6%81%E6%B1%82%E7%9A%84%E5%87%BD%E6%95%B0%E4%B8%8D%E5%8F%97%E6%94%AF%E6%8C%8102.png)

2.选择计算机配置>管理模板>系统>凭据分配>加密Oracle修正。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%BF%9C%E7%A8%8B%E6%8F%90%E7%A4%BA%E5%87%BA%E7%8E%B0%E8%BA%AB%E4%BB%BD%E9%AA%8C%E8%AF%81%E9%94%99%E8%AF%AF%EF%BC%8C%E8%A6%81%E6%B1%82%E7%9A%84%E5%87%BD%E6%95%B0%E4%B8%8D%E5%8F%97%E6%94%AF%E6%8C%8103.png)

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%BF%9C%E7%A8%8B%E6%8F%90%E7%A4%BA%E5%87%BA%E7%8E%B0%E8%BA%AB%E4%BB%BD%E9%AA%8C%E8%AF%81%E9%94%99%E8%AF%AF%EF%BC%8C%E8%A6%81%E6%B1%82%E7%9A%84%E5%87%BD%E6%95%B0%E4%B8%8D%E5%8F%97%E6%94%AF%E6%8C%8104.png)

3.选择启用并选择易受攻击。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%BF%9C%E7%A8%8B%E6%8F%90%E7%A4%BA%E5%87%BA%E7%8E%B0%E8%BA%AB%E4%BB%BD%E9%AA%8C%E8%AF%81%E9%94%99%E8%AF%AF%EF%BC%8C%E8%A6%81%E6%B1%82%E7%9A%84%E5%87%BD%E6%95%B0%E4%B8%8D%E5%8F%97%E6%94%AF%E6%8C%8105.png)

该问题同样适用于远程登陆云主机后再次输入密码的情况（输入两次密码的问题）：将加密Oracle修正由未配置改为已启用，并将保护级别设置为易受攻击。



如无法解决您的问题，请向我们提工单。
