# FTP报Error code 451处理方法
**现象描述**

使用Windows Server IIS搭建的FTP服务器在上传文件夹或者文件的时候，如果文件夹或者文件名称中英文混和，则会出现以下错误提示框：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/FTP%E6%8A%A5Error%20code%20451%E5%A4%84%E7%90%86%E6%96%B9%E6%B3%9501.png)

**处理步骤**

1.点击任务栏左下角红框处启动“服务器管理器”，点击右上角红框处工具按钮，选择IIS管理器。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/FTP%E6%8A%A5Error%20code%20451%E5%A4%84%E7%90%86%E6%96%B9%E6%B3%9502.png)

2.在IIS管理器左侧网站页面逐级选择FTP站点，点击右侧红框处高级设置。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/FTP%E6%8A%A5Error%20code%20451%E5%A4%84%E7%90%86%E6%96%B9%E6%B3%9503.png)

3. 将“允许UTF8”从 “True” 改为 “False”，点击确定。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/FTP%E6%8A%A5Error%20code%20451%E5%A4%84%E7%90%86%E6%96%B9%E6%B3%9504.png)

4. 点击右侧红框处**重新启动**按钮即可重启服务器， 问题可以得到解决。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/FTP%E6%8A%A5Error%20code%20451%E5%A4%84%E7%90%86%E6%96%B9%E6%B3%9505.png)
