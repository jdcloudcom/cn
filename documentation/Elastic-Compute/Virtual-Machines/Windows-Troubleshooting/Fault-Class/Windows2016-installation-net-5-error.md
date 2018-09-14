# Windows2016安装.net3.5报错
**问题现象：**

默认下安装.net3.5会安装失败，提示找不到源文件。如图：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2016%E5%AE%89%E8%A3%85.net3.5%E6%8A%A5%E9%94%9901.png)

**问题原因：**

Windows update服务没有运行导致。



**解决方法：**

开始菜单运行执行services.msc回车，找到windows update服务。默认是禁用，改成手动并启动。然后在线安装.net3.5组件，安装完毕后可以视需求，停止及禁用windows update服务。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2016%E5%AE%89%E8%A3%85.net3.5%E6%8A%A5%E9%94%9902.png)

如无法解决您的问题，请向我们提工单。
