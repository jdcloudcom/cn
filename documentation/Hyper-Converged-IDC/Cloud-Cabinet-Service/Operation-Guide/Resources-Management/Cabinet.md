# 机柜

1. 打开控制台，选择超融合数据中心->云托管服务->资源管理->机柜，进入机柜列表页，展示京东云为客户分配的机柜信息，如下图：
![机柜列表查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS004.png)

2. 机房：默认选择某一个机房，如果有多个机房，支持不同机房类型切换选择，切换后列表显示不同机柜信息；
 ![地域区查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS005.png)
 
3. 机柜列表，字段如下：
 - 机柜编码：指机柜的编码，是机柜的唯一标识
 
 - 房间号：指机房的房间号
 
 - 机柜空间:指机房的高度，单位为U
 
 - 机柜类型：指机柜的类型，目前只有正式机柜一种类型
 
 - 机柜状态：指机柜是否加电，包括未加电和已加电。支持按照机柜状态“未加电”、“已加电”筛选
 
 - 额定电流：指机柜的额定电流，单位为A
 
 - 起租时间：指机柜的开始计费时间
 
 - 到期时间：指机柜的到期时间 
 
 4.  机柜详情，点击“机柜编码”，跳转到机柜详情，机柜详情展示2部分，包括基本信息和设备列表，如下图：
 ![机柜详情页查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS006.png)
 
 - 基本信息：展示机柜的详细信息。
 
   - 机房名称：指客户选择的托管机房
  
   - 占用U数: 指该机柜托管设备占用的机柜总U数
  
   - 空闲U数: 指除去该机柜所有托管设备占用的机柜U数，（空闲U数=机柜空间-占用U数，） 。空闲U数不能作为衡量该机柜还可托管设备数量的依据，需参考现场实际布局
  
   - 其余字段说明详见[机柜列表]()
  
 - 设备信息：展示该机柜所有的托管设备。
 
   - SN号：指设备的SN号，设备的唯一标识。点击“SN号”，跳转到设备详情页，详见[设备详情]()
  
   - 所在U位：指设备所在机柜的位置。例如：12-15，说明从第12U到15U，占了3U空间
  
   - 品牌: 指该设备的品牌
  
   - 型号：指该设备的型号
  
   - 设备类型：指设备的类型，包括服务器、存储设备、网络设备、其他设备等<br />
  
 5.点击“刷新”按钮，您可以对机柜列表进行刷新操作。
 ![刷新按钮查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS007.png)
 
 6.在搜索框中输入“机柜编号”，然后单击搜索图标即可查询符合搜索条件的结果。
 ![机柜列表搜索框查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS008.png)
 
 7.点击“自定义列表字段项”按钮，可选择要显示的字段，“机柜编码”字段不可取消，最多勾选8个字段，包括的字段如下：机柜编码、房间号、机柜空间、机柜类型、机柜状态、机柜电源、起租时间、到期时间。
 ![机柜列表自定义按钮查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS009.png)
 ![机柜列表自定义弹框查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS010.png)
 
 8.点击“导出”按钮，可以导出全部列表的内容。
 ![机柜列表导出查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS011.png)
   
