# Windows2008磁盘分区和格式化
注意：磁盘分区和格式化是高风险行为，请慎重操作。如下操作是针对新购买的数据盘，如果涉及到原有数据盘的处理，请务必对云主机的数据盘创建快照以避免可能的数据丢失。



**购买数据盘后，默认是没有分区、格式化的，您可以参考以下方法来进行初始配置：**

1.点击左下角的服务器管理器。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E7%A3%81%E7%9B%98%E5%88%86%E5%8C%BA%E5%92%8C%E6%A0%BC%E5%BC%8F%E5%8C%9601.png)

2.选择【存储】--【磁盘管理】。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E7%A3%81%E7%9B%98%E5%88%86%E5%8C%BA%E5%92%8C%E6%A0%BC%E5%BC%8F%E5%8C%9602.png)

3.右键点击数据盘（磁盘1），选择初始化磁盘。选择MBR（主启动记录），确定。

注：此时如果数据盘显示“脱机”，需先在磁盘1处右键点击“联机”再进行后续操作。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E7%A3%81%E7%9B%98%E5%88%86%E5%8C%BA%E5%92%8C%E6%A0%BC%E5%BC%8F%E5%8C%9603.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E7%A3%81%E7%9B%98%E5%88%86%E5%8C%BA%E5%92%8C%E6%A0%BC%E5%BC%8F%E5%8C%9604.png)

4.在空白分区上，右键选择【新建简单卷】。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E7%A3%81%E7%9B%98%E5%88%86%E5%8C%BA%E5%92%8C%E6%A0%BC%E5%BC%8F%E5%8C%9605.png)

5.默认下一步。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E7%A3%81%E7%9B%98%E5%88%86%E5%8C%BA%E5%92%8C%E6%A0%BC%E5%BC%8F%E5%8C%9606.png)
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E7%A3%81%E7%9B%98%E5%88%86%E5%8C%BA%E5%92%8C%E6%A0%BC%E5%BC%8F%E5%8C%9607.png)

6.选择数据盘挂载的盘符，下一步。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E7%A3%81%E7%9B%98%E5%88%86%E5%8C%BA%E5%92%8C%E6%A0%BC%E5%BC%8F%E5%8C%9608.png)

7.选择文件系统为NTFS，勾选执行快速格式化。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E7%A3%81%E7%9B%98%E5%88%86%E5%8C%BA%E5%92%8C%E6%A0%BC%E5%BC%8F%E5%8C%9609.png)

8.点击【完成】，系统会自动设置好新的分区。数据盘挂载盘符格式化完毕。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows2008%E7%A3%81%E7%9B%98%E5%88%86%E5%8C%BA%E5%92%8C%E6%A0%BC%E5%BC%8F%E5%8C%9610.png)

如无法解决您的问题，请向我们提工单。
