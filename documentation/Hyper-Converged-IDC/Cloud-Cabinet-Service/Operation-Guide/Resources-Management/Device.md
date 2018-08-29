# 设备

1. 打开控制台，选择超融合数据中心->云托管服务->资源管理->设备，进入设备列表页，展示京东云为客户分配的设备信息，如下图：

![设备列表查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS012.png)

2. 机房：默认选择某一个机房，如果有多个机房，支持不同机房类型切换选择，切换后列表显示不同设备信息；

![地域区查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS005.png)

3. 设备列表，字段如下：

- SN号：设备的SN号，是设备的唯一标识

- 机柜编码：机柜的编码，是机柜的唯一标识

- U位:指设备所在机房的位置。例如，12-15，说明从第12U到15U，占了3U空间

- 设备类型: 指设备的类型，包括服务器、存储设备、网络设备、其他设备。支持按照设备类型筛选

- 设备状态：指设备的状态，包括已入库和已上架。支持按照设备状态“已入库”、“已上架”筛选

4. 设备详情，点击“SN号”，跳转到设备详情，设备详情展示3部分，包括基本信息、所属信息和配置信息，如下图：
![设备详情查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS013.png)

- 基本信息：展示设备的详细信息。

  - 品牌：指该设备的品牌
  
  - 型号：指该设备的型号
  
  - 其余字段说明详见[设备列表]()
  
- 所属信息

  - 所属机房：指该设备所属的托管机房
  
  - 资产所属：目前支持自备，指客户自己的设备
  
- 配置信息

  - CPU逻辑核数：指设备的CPU核数
  
  - 内存总容量：指设备的内存总容量
  
  - 硬盘总容量：指设备的磁盘总容量
  
  - 网卡带宽：指设备的网卡带宽
  
5. 点击“刷新”按钮，您可以对设备列表进行刷新操作。
![刷新按钮查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS007.png)

6. 在搜索框中输入“SN号”，然后单击搜索图标即可查询符合搜索条件的结果。
![设备搜索框查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS014.png)

7. 点击“自定义列表字段项”按钮，可选择要显示的字段，“SN号”字段不可取消，最多勾选7个字段，包括的字段：SN号、机柜编码、所在U位、设备类型、设备状态、品牌、型号。
![自定义按钮查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS009.png)
![自定义弹框查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS015.png)

8. 点击“导出”按钮，可以导出全部列表的内容。
![导出按钮查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS011.png)
