# Windows系统云硬盘状态外部或脱机
**问题现象：**

在计算机，磁盘管理里看到云硬盘是外部或脱机状态。如图：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E4%BA%91%E7%A1%AC%E7%9B%98%E7%8A%B6%E6%80%81%E5%A4%96%E9%83%A8%E6%88%96%E8%84%B1%E6%9C%BA01.png)

**解决方法：**

1.如果显示为外部的磁盘，在磁盘区块上右击选择导入外部磁盘，然后点击确定即可。如图：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E4%BA%91%E7%A1%AC%E7%9B%98%E7%8A%B6%E6%80%81%E5%A4%96%E9%83%A8%E6%88%96%E8%84%B1%E6%9C%BA02.png)

2.如果显示为脱机的磁盘，在磁盘区块上右击选择联机。如图：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9F%E4%BA%91%E7%A1%AC%E7%9B%98%E7%8A%B6%E6%80%81%E5%A4%96%E9%83%A8%E6%88%96%E8%84%B1%E6%9C%BA03.png)

说明：在选择联机的过程中，可能会出现以下提示：

该磁盘处于脱机状态，因为它与另外一个联机磁盘发生签名冲突

出现该问题说明 Windows 在自动挂载过程中出现了异常，可以尝试先将磁盘脱机，然后再联机。Windows 在联机过程中会尝试重新生成磁盘的签名。



如无法解决您的问题，请向我们提工单。
