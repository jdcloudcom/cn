# Windows远程连接提示没有授权许可证
Windows 服务器默认提供两个用户的免费远程桌面管理授权。如果有更高的连接需求，需要在微软官网购买和配置相应的证书授权。

**问题现象：**

远程桌面客户端连接 Windows 实例时，输入正确的用户名和密码提交后，无法正常远程连接，并出现如下错误信息：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%BF%9C%E7%A8%8B%E8%BF%9E%E6%8E%A5%E6%8F%90%E7%A4%BA%E6%B2%A1%E6%9C%89%E6%8E%88%E6%9D%83%E8%AE%B8%E5%8F%AF%E8%AF%8101.png)

使用控制台远程连接vnc功能登录到 Windows 云主机后， 打开RD授权诊断程序，出现如下错误信息：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%BF%9C%E7%A8%8B%E8%BF%9E%E6%8E%A5%E6%8F%90%E7%A4%BA%E6%B2%A1%E6%9C%89%E6%8E%88%E6%9D%83%E8%AE%B8%E5%8F%AF%E8%AF%8102.png)

**问题分析：**


该问题可能有由于以下两种原因：

● 他人登录

可能是该账号已经有人登录，由于终端服务配置 RDP-Tcp 限制了每个用户只能进行一个会话，所以其他会话无法建立。



● 安装了远程桌面会话主机角色

可能是由于在系统内部安装了远程桌面会话主机角色。此功能是前 120 天免费的，过期就要付费，如没有续费会导致远程连接不上。

正常情况下，Windows 服务器默认提供两个用户的免费远程桌面管理授权。如果有更高的连接需求，则需要配置远程桌面会话主机服务器角色，同时购买和配置相应的授权后，才可以使用更多的远程桌面管理并发。

另一方面，在配置远程桌面会话主机角色后，会同时取消原有默认的 2 个免费连接授权。所以，在没有正确配置相关授权的时候，会导致远程桌面无法连接，并出现上述错误提示。



**解決方法：**

● 他人登录

可以通过取消 RDP-Tcp 限制每个用户只能进行一个会话的方法：

1.使用控制台远程连接vnc功能登录到 Windows 云主机。选择开始 > 控制面板 > 管理工具 > 服务器管理器。

2.在远程桌面服务页面，双击远程桌面会话主机配置。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%BF%9C%E7%A8%8B%E8%BF%9E%E6%8E%A5%E6%8F%90%E7%A4%BA%E6%B2%A1%E6%9C%89%E6%8E%88%E6%9D%83%E8%AE%B8%E5%8F%AF%E8%AF%8103.png)

3.在弹出的窗口中，将选项限制每个用户只能进行一个会话设置为否，重新连接即可。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%BF%9C%E7%A8%8B%E8%BF%9E%E6%8E%A5%E6%8F%90%E7%A4%BA%E6%B2%A1%E6%9C%89%E6%8E%88%E6%9D%83%E8%AE%B8%E5%8F%AF%E8%AF%8104.png)

● 安装了远程桌面会话主机角色

安装远程桌面会话主机导致的无法远程的解决办法有二种：

**方法一**

在配置远程桌面会话主机服务器后，在微软官网购买和配置相应的证书授权，相关操作方法可以参阅微软官方文档。



**方法二**

删除远程桌面会话主机角色，使用默认的 2 个免费连接授权。参考以下几个章节对不同版本的服务器进行配置：




**Windows 2012 系统操作方法**

1.使用控制台远程连接vnc功能登录到 Windows 云主机。

2.选择开始>控制面板>管理工具>服务器管理器。

3.在页面右上角，选择管理>删除角色。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%BF%9C%E7%A8%8B%E8%BF%9E%E6%8E%A5%E6%8F%90%E7%A4%BA%E6%B2%A1%E6%9C%89%E6%8E%88%E6%9D%83%E8%AE%B8%E5%8F%AF%E8%AF%8105.png)

4.在删除功能和角色窗口，单击下一步，然后再单击下一步。

5.在向导第三步，取消勾选远程桌面服务，其它默认配置。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%BF%9C%E7%A8%8B%E8%BF%9E%E6%8E%A5%E6%8F%90%E7%A4%BA%E6%B2%A1%E6%9C%89%E6%8E%88%E6%9D%83%E8%AE%B8%E5%8F%AF%E8%AF%8106.png)

6.完成以上操作后重启服务器即可。



**Windows 2008 系统操作方法**

1.使用控制台远程连接vnc功能登录到 Windows 云主机。选择开始 > 控制面板 > 管理工具 > 服务器管理器。

2.在服务器管理器窗口，右键单击远程桌面服务 ，选择删除角色服务。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%BF%9C%E7%A8%8B%E8%BF%9E%E6%8E%A5%E6%8F%90%E7%A4%BA%E6%B2%A1%E6%9C%89%E6%8E%88%E6%9D%83%E8%AE%B8%E5%8F%AF%E8%AF%8107.png)

3.在弹出窗口中，取消远程桌面会话主机勾选，单击下一步直到完成。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E8%BF%9C%E7%A8%8B%E8%BF%9E%E6%8E%A5%E6%8F%90%E7%A4%BA%E6%B2%A1%E6%9C%89%E6%8E%88%E6%9D%83%E8%AE%B8%E5%8F%AF%E8%AF%8108.png)

4.完成以上操作后重启服务器即可。



如无法解决您的问题，请向我们提工单。
