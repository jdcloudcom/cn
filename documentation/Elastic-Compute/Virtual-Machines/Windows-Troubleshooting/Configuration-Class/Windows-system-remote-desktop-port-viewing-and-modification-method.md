# Windows系统远程桌面端口查看和修改方法
**如何查看Windows远程桌面的端口：**

1.通过命令查看，点击 开始 - 运行 - 输入 cmd，确认 后打开命令窗口，执行如下命令：

***tasklist /svc | find "Ter"***

可以看到 TermService 的进程 ID 是 1764。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E8%BF%9C%E7%A8%8B%E6%A1%8C%E9%9D%A2%E7%AB%AF%E5%8F%A3%E6%9F%A5%E7%9C%8B%E5%92%8C%E4%BF%AE%E6%94%B9%E6%96%B9%E6%B3%9501.png)

再执行如下命令：

***netstat -ano | find "1764"***

即可看到服务所使用的端口，如下图所示是 3389

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E8%BF%9C%E7%A8%8B%E6%A1%8C%E9%9D%A2%E7%AB%AF%E5%8F%A3%E6%9F%A5%E7%9C%8B%E5%92%8C%E4%BF%AE%E6%94%B9%E6%96%B9%E6%B3%9502.png)

2.打开注册表查看，在 运行 中输入 *regedit* 打开注册表编辑器。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E8%BF%9C%E7%A8%8B%E6%A1%8C%E9%9D%A2%E7%AB%AF%E5%8F%A3%E6%9F%A5%E7%9C%8B%E5%92%8C%E4%BF%AE%E6%94%B9%E6%96%B9%E6%B3%9503.png)

查看HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server\Wds\rdpwd\Tds\tcp  PortNumber 子键的值，如下图所示：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E8%BF%9C%E7%A8%8B%E6%A1%8C%E9%9D%A2%E7%AB%AF%E5%8F%A3%E6%9F%A5%E7%9C%8B%E5%92%8C%E4%BF%AE%E6%94%B9%E6%96%B9%E6%B3%9504.png)

还需要查看 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp 下 portnumber 的值，两个值正常是相同的，就是远程服务的端口。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E8%BF%9C%E7%A8%8B%E6%A1%8C%E9%9D%A2%E7%AB%AF%E5%8F%A3%E6%9F%A5%E7%9C%8B%E5%92%8C%E4%BF%AE%E6%94%B9%E6%96%B9%E6%B3%9505.png)

**如何修改Windows远程桌面的端口：**

1.开始 - 运行 中输入 *regedit* 打开注册表编辑器。

2.依次展开 "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TerminalServer\Wds\rdpwd\Tds\tcp" 注册表项。其下的 PortNumber 键值所对应的端口号就是远程桌面端口，将其修改为用户需要的端口即可，如下图所示：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E8%BF%9C%E7%A8%8B%E6%A1%8C%E9%9D%A2%E7%AB%AF%E5%8F%A3%E6%9F%A5%E7%9C%8B%E5%92%8C%E4%BF%AE%E6%94%B9%E6%96%B9%E6%B3%9506.png)

3.再依次展开注册表中 "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TerminalServer\WinStations\RDP-Tcp" 注册表项。同样按照上面的方法将 PortNumber 键值进行更改保存，如下图所示：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E8%BF%9C%E7%A8%8B%E6%A1%8C%E9%9D%A2%E7%AB%AF%E5%8F%A3%E6%9F%A5%E7%9C%8B%E5%92%8C%E4%BF%AE%E6%94%B9%E6%96%B9%E6%B3%9507.png)

注意：修改后需要检查防火墙、tcp/ip筛选中是否有安全规则限制，并需要重启服务器后生效。

如无法解决您的问题，请向我们提工单。
