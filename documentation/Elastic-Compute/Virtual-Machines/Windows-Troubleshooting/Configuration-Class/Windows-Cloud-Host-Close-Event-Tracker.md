# Windows云主机关闭事件跟踪程序
Windows系统云主机在异常重启后再次登陆时会弹出事件跟踪程序提示框，关闭事件追踪程序是指在系统非正常关机后再次开机时会显示“关闭事件跟踪程序”对话框，以询问用户非正常关机的原因。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E4%BA%91%E4%B8%BB%E6%9C%BA%E5%85%B3%E9%97%AD%E4%BA%8B%E4%BB%B6%E8%B7%9F%E8%B8%AA%E7%A8%8B%E5%BA%8F01.png)

如果您不希望跟踪这类事件，可以关闭事件跟踪程序。

第1步，打开“组策略编辑器”窗口(运行--*gpedit.msc*)，在左窗格中依次展开“计算机配置”→“管理模板”目录。然后选中“系统”选项，并在右窗格中双击“显示关闭事件追踪程序”策略选项。

第2步，在打开的“显示关闭事件追踪程序 属性”对话框中选中“已禁用”单选框，并单击“确定”按钮使设置生效。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E4%BA%91%E4%B8%BB%E6%9C%BA%E5%85%B3%E9%97%AD%E4%BA%8B%E4%BB%B6%E8%B7%9F%E8%B8%AA%E7%A8%8B%E5%BA%8F02.png)

