# Windows系统如何取消登录显示组合键
**问题描述:**

Windows系统服务器通过控制台远程连接功能登录的时候会提示"按ctrl+alt+del 登录" ，如何取消此提示。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E5%A6%82%E4%BD%95%E5%8F%96%E6%B6%88%E7%99%BB%E5%BD%95%E6%98%BE%E7%A4%BA%E7%BB%84%E5%90%88%E9%94%AE01.png)

**解决方案:**

登录服务器，点击 开始 - 运行，输入 gpedit.msc，打开 组策略编辑器。在组策略编辑器的左框内依次序展开 计算机配置 - Windows 设置 - 安全设置 - 本地策略 - 安全选项，点击 安全选项 找到 交互式登录:无需按 CTRL+ALT+DEL 右键点击该项，在弹出的菜单中选择下 已启用，然后关闭窗口，之后将登录注销下，再次进入便不会显示输入ctrl+alt+del 的提示了。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E5%A6%82%E4%BD%95%E5%8F%96%E6%B6%88%E7%99%BB%E5%BD%95%E6%98%BE%E7%A4%BA%E7%BB%84%E5%90%88%E9%94%AE02.png)
