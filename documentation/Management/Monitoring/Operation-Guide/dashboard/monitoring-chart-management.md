## 管理监控图表
### 图表配置项说明
#### 图表类型
目前Dashboard支持折线图和TopN表格两种展示类型。

**折线图：** 满足用户绝大部分的监控需求。按照时间的顺序展示。例如某标签下的所有云主机实例在当天13：00-15：001的CPU使用率的变化情况。折线图可添加多个监控项。

**TopN表格：** 实时显示监控项数据值由大到小的排序。例如某标签下的所有云主机实例的 CPU 使用率从大到小的排序。TopN表格只能添加一个监控项。

#### 视图维度
目前dashboard支持的数据展示维度包括明细和汇总。

**明细：** 一个云资源的一个监控项为一条数据线。在同一张图表中显示多个云资源以及对应的所有监控项。图表中的数据线的条数等于所监控的云资源的数量乘以监控项的数量。

**汇总：** 多个云资源的相同监控项汇总为一条数据线。在同一张图表中显示多个监控项的汇总数据。图标中的数据线的条数等于所监控的监控项的数量。聚合方式包括：最大值、最小值和平均值。

#### 高级配置
设置高级配置后，所选维度下全部资源，包括新增资源的监控数据将会直接在该图表中显示，无需手动添加。
当前高级配置仅有标签，标签仅支持“云主机”、“云硬盘”和“云数据库-SQLSERVER”，若产品类型选择为其他资源时，则没有高级配置选项。

### 添加监控图表
1.进入监控面板详情页，点击右上角的“添加图表“。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Cloud-Monitor/dashboard/%E6%B7%BB%E5%8A%A0%E5%9B%BE%E8%A1%A8.png)

2.选择图表类型、产品类型、视图维度、监控项（支持添加多个监控项）、图表名称，选择监控资源，点击“确定”按钮，完成监控图表的创建。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Cloud-Monitor/zuijiashijian/%E6%9C%80%E4%BD%B3%E5%AE%9E%E8%B7%B51.2.png)

### 删除监控图表
1.点击图表中的“删除”。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Cloud-Monitor/dashboard/%E5%88%A0%E9%99%A4%E7%9B%91%E6%8E%A7%E5%9B%BE%E8%A1%A8.png)

2.弹框提示是否删除监控图表，点击确定，删除监控图表完成。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Cloud-Monitor/dashboard/%E5%88%A0%E9%99%A4%E7%9B%91%E6%8E%A7%E5%9B%BE%E8%A1%A8-%E7%A1%AE%E8%AE%A4.png)

### 复制监控图表
点击图表中的“复制”选项，即可快速打开添加监控图页面。复制打开的添加监控图页面与原监控图表各项配置及监控资源完全相同的监控图表，可以对图表的配置及监控资源进行调整，点击确定，生成一张新的监控图表。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Cloud-Monitor/dashboard/%E5%A4%8D%E5%88%B6%E7%9B%91%E6%8E%A7%E5%9B%BE%E8%A1%A8.png)

### 时间筛选
1.点击图表中的时间图标。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Cloud-Monitor/dashboard/%E6%97%B6%E9%97%B4%E7%AD%9B%E9%80%89.png)

2.选择自己想要查看的时间范围，同时也可以自定义需要查看的时间范围。
![](https://github.com/jdcloudcom/cn/blob/edit/image/Cloud-Monitor/dashboard/%E6%97%B6%E9%97%B4%E7%AD%9B%E9%80%892.png)


### 导出数据
1.在小图点击导出数据选项或在放大图中点击“导出”图标。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Cloud-Monitor/dashboard/%E5%AF%BC%E5%87%BA%E6%95%B0%E6%8D%AE.png)

2.若图表类型为折线图，导出的数据可选择“图表选中的时间段”或“当前查看的时间点”，若图标类型为TopN图，则直接导出监控图设置的时间段。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Cloud-Monitor/dashboard/%E5%AF%BC%E5%87%BA%E6%95%B0%E6%8D%AE2.png)
