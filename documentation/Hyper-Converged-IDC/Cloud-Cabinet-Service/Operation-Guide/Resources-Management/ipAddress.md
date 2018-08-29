# 公网IP
1. 打开控制台，选择超融合数据中心->云托管服务->资源管理->机柜，进入机柜列表页，展示京东云为客户分配的机柜信息，如下图：
![公网IP列表查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS016.png)

2. 机房，默认选择某一个机房，如果有多个机房，支持不同机房类型切换选择，切换后列表显示不同公网IP地址信息；
![地域区查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS005.png)

3. 公网IP列表，字段如下：
  - IP地址段：指为客户分配的公网IP地址
  - 网络位地址：指为客户分配的网络位地址
  - 网关地址: 指为客户分配的网络位地址
  - 广播地址：指为客户分配的网络位地址
  - 可用地址空间：指为客户分配的可用IP地址
  - 状态：指该公网IP的状态，一般为正常，即可用<br />
  另外，对于服务器可以用IP地址计算上，因为要除去网络位占用1个，广播位占用1个，还需要客户拿出1个IP做网关，支持的服务器数量要减去3，请知悉。

4. 点击“刷新”按钮，您可以对公网IP列表进行刷新操作。
![刷新按钮查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS007.png)

5. 在搜索框中输入“IP地址段”，然后单击搜索图标即可查询符合搜索条件的结果。
![公网IP列表搜索框查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS017.png)
6. 点击“自定义列表字段项”按钮，可选择要显示的字段，“IP地址段”不可取消，最多勾选6个字段，包括的字段：IP地址段、网络位地址、网关地址、广播地址、可用地址空间、状态。
![自定义按钮查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS009.png)
![自定义弹框查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS018.png)

7. 点击“导出”按钮，可以导出全部列表的内容。![导出查看连接](https://github.com/jdcloudcom/cn/blob/cn-Cloud-Cabinet-Service/image/Hyper-Converged-IDC/Cloud-Cabinet-Service/CCS011.png)

