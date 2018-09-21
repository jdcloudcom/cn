## 使用自定义监控
自定义监控是提供给用户自由定义监控项及报警规则的一项功能。通过此功能，用户可以针对自己关心的业务指标进行监控，将采集到监控数据上报至云监控，由云监控来进行数据的处理，并根据结果进行报警。
### 上报监控数据
自定义监控功能为您提供上报监控数据的接口，方便您将自己采集的时序数据上报到云监控。目前支持OpenAPI的方式进行上报，可上报原始数据和已聚合的统计数据。
点击查看如何[上报监控数据](http://docs.jdcloud.com/cn/monitoring/reporting-monitoring-data)。
### 查看监控数据
**查看命名空间**

进入京东云控制台-云监控-自定义监控，进入自定义监控主页面，可查看到您已上报的命名空间、监控对象及指标情况。如下图所示：
![](https://raw.githubusercontent.com/jdcloudcom/cn/edit/image/Cloud-Monitor/1.%E5%91%BD%E5%90%8D%E7%A9%BA%E9%97%B4.png)
**查看监控资源**

点击命名空间的名称，可查看上报到属于该名称空间的资源情况，如下图所示：
![](https://raw.githubusercontent.com/jdcloudcom/cn/edit/image/Cloud-Monitor/2.%E7%9B%91%E6%8E%A7%E5%AF%B9%E8%B1%A1%E5%88%97%E8%A1%A8.png)
**查看监控图表**

选中要查看的监控对象，点击操作列的“监控表”，进入监控图表详情页，可查看该监控对象的监控趋势图，如下图所示：
![](https://raw.githubusercontent.com/jdcloudcom/cn/edit/image/Cloud-Monitor/3.%E7%9B%91%E6%8E%A7%E5%9B%BE.png)
### 删除监控数据
进入京东云控制台-云监控-自定义监控，进入自定义监控主页面。点击命名空间的名称，进入监控资源列表页面，选中要删除的监控对象，点击操作列的“删除”按钮，即可删除。

注：若删除命名空间下的全部监控对象之后，命名空间也级联删除了。
