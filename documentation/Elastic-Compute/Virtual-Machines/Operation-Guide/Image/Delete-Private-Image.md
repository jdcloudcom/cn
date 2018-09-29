# 删除私有镜像

## 前提条件
* 仅“可用”或“错误”状态的私有镜像支持删除。

## 注意事项
* 已共享的私有镜像在取消共享关系前不可删除，如私有镜像已共享给其他用户，请取消共享后再进行删除。

## 操作步骤
1. 访问[镜像控制台][1]，或访问[京东云控制台](https://console.jdcloud.com/overview)点击左侧导航栏【弹性计算】-【云主机】-【镜像】进入镜像列表页。
2. 选择“私有镜像”TAB，找到要删除的私有镜像，在私有镜像列表中选择【删除】操作。
![](../../../../../image/vm/Operation-Guide-Image-delete1.png)

3. 在确认删除弹出框中，点击【确认】，即可删除私有镜像。如私有镜像包含设备映射信息，则删除镜像不会删除与其关联的云硬盘快照，如需删除快照请前往云硬盘快照页面进行删除。
![](../../../../../image/vm/Operation-Guide-Image-delete2.png)



  [1]: https://cns-console.jdcloud.com/host/image/list
  [3]: ./images/Operation-Guide-Image-delete1.png "Operation-Guide-Image-delete1.png"
  [4]: ./images/Operation-Guide-Image-delete2.png "Operation-Guide-Image-delete2.png"