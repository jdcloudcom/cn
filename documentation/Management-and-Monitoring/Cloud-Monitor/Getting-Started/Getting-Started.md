## 入门指南概述
该部分主要描述如何快速查看云资源的监控图表，以及针对某个云资源设置报警规则，查看报警规则和报警历史。

## 查看云资源监控图表
云资源的监控图表可通过两种方式进行查看，一种是在云监控页面进行查看，一种是在资源内查看。
### 云监控页面查看
1. 进入京东云控制台-云监控菜单，可看到各资源的监控列表。

![image](https://raw.githubusercontent.com/jdcloudcom/cn/edit/image/Cloud-Monitor/yunziyuan/1.%E8%B5%84%E6%BA%90%E7%9B%91%E6%8E%A7.png)

2. 点击各实例的操作列的“监控表”，即可看到该实例各指标的监控数据。

![image](https://raw.githubusercontent.com/jdcloudcom/cn/edit/image/Cloud-Monitor/yunziyuan/2.%E8%B5%84%E6%BA%90%E7%9B%91%E6%8E%A7.png)

### 资源内查看
1. 进入京东云控制台，可进入云监控支持的云产品管理页，点击某一资源查看详情。

![image](https://raw.githubusercontent.com/jdcloudcom/cn/edit/image/Cloud-Monitor/yunziyuan/3.%E8%B5%84%E6%BA%90%E7%9B%91%E6%8E%A7.png)

2. 点击“监控”进入该资源的监控页面，即可看到该实例各指标的监控数据。


## 设置报警规则
### 增加报警规则
1. 进入京东云控制台-云监控菜单，可看到各资源的监控列表，点击各实例的操作列的“报警规则”。点击“新增报警规则”，可以创建报警规则。
 
![image](https://raw.githubusercontent.com/jdcloudcom/cn/edit/image/Cloud-Monitor/yunziyuan/4.%E8%B5%84%E6%BA%90%E7%9B%91%E6%8E%A7.png)

2. 输入监控项、统计周期、统计方法、计算方式、阈值、持续周期，根据业务需求也可设置分级报警，分为（一般，紧急添加报警规则及联系人，点击“确定”。 

![image](https://raw.githubusercontent.com/jdcloudcom/cn/edit/image/Cloud-Monitor/yunziyuan/5.%E8%B5%84%E6%BA%90%E7%9B%91%E6%8E%A7.png)

3. 创建成功，则相关信息更新；若创建失败，则出现提示框，如果多次创建失败，请联系客服。

### 修改/删除/禁用报警规则
1. 进入京东云控制台-云监控菜单，找到需要进行修改的报警规则实例，点击“报警规则”；
修改监控规则：根据需要修改监控项、统计周期、统计方法、计算方式、阈值、持续周期、报警联系人，点击“确定”；
2. 删除监控规则：点击相应报警规则后面的X，即可删除。
3. 禁用报警规则：点击相应报警规则中的“禁用”，即可禁用规则。

![image](https://raw.githubusercontent.com/jdcloudcom/cn/edit/image/Cloud-Monitor/yunziyuan/6.%E8%B5%84%E6%BA%90%E7%9B%91%E6%8E%A7.png)

### 管理报警联系人/组
登录京东云账号后，在页面右上侧查看账户信息下拉框，点击账号管理-联系人管理，可在此页面查看并管理联系人及联系组。

![image](https://raw.githubusercontent.com/jdcloudcom/cn/edit/image/Cloud-Monitor/yunziyuan/7.%E8%B5%84%E6%BA%90%E7%9B%91%E6%8E%A7.png)

### 添加/使用报警模板
1. 进入京东云控制台-云监控菜单，找到需要进行修改的报警规则实例，点击“报警规则”；在该页面中点击新增报警规则，根据需要修改监控项、统计周期、统计方法、计算方式、阈值、持续周期，完成后勾选“保存为新的报警规则模板”将该规则保存为模板。

![image](https://raw.githubusercontent.com/jdcloudcom/cn/edit/image/Cloud-Monitor/yunziyuan/8.%E8%B5%84%E6%BA%90%E7%9B%91%E6%8E%A7.png)

2. 已有报警模板后，可在新增报警规则页面，勾选“使用已有的报警规则模板”选择已有模板进行使用。
 
![image](https://raw.githubusercontent.com/jdcloudcom/cn/edit/image/Cloud-Monitor/yunziyuan/9.%E8%B5%84%E6%BA%90%E7%9B%91%E6%8E%A7.png)

## 使用Dashboard监控面板
提供用户自定义监控数据展示的功能。用户可以将关注的核心服务监控指标集中呈现在一张监控面板里，满足大盘盯屏展示，批量实例汇总展示、故障排障、数据对比分析等场景。

### 添加监控面板
1.登录京东云云监控控制台dashboard下的监控面板页面。
2.点击左上角的“创建面板”。
3.填写监控面板名称，点击确定完成创建。
![](https://raw.githubusercontent.com/jdcloudcom/cn/edit/image/Cloud-Monitor/zuijiashijian/%E6%9C%80%E4%BD%B3%E5%AE%9E%E8%B7%B51.1.png)
### 添加监控图表
1. 进入监控面板详情页，点击右上角的“添加图表“。
2. 选择图表类型。
3. 选择监控资源类型。
4. 选择视图维度。
5. 添加监控项，支持添加多个监控项。
6. 填写图表名称。
7. 选择监控资源，支持以标签为维度筛选。
8. 点击确定，完成监控图表的创建。
![](https://raw.githubusercontent.com/jdcloudcom/cn/edit/image/Cloud-Monitor/zuijiashijian/%E6%9C%80%E4%BD%B3%E5%AE%9E%E8%B7%B51.2.png)
### 查看dashboard监控图表
进入监控面板详情页查看监控图表。
![](https://raw.githubusercontent.com/jdcloudcom/cn/edit/image/Cloud-Monitor/zuijiashijian/%E6%9C%80%E4%BD%B3%E5%AE%9E%E8%B7%B51.3.png)

## 使用自定义监控
自定义监控是提供给用户自由定义监控项及报警规则的一项功能。通过此功能，用户可以针对自己关心的业务指标进行监控，将采集到监控数据上报至云监控，由云监控来进行数据的处理，并根据结果进行报警。
### 上报监控数据
自定义监控功能为您提供上报监控数据的接口，方便您将自己采集的时序数据上报到云监控。目前支持OpenAPI的方式进行上报，可上报原始数据和已聚合的统计数据。
点击查看如何[上报监控数据](https://github.com/jdcloudcom/cn/blob/edit/documentation/Management-and-Monitoring/Cloud-Monitor/Operation-Guide/%E8%87%AA%E5%AE%9A%E4%B9%89%E7%9B%91%E6%8E%A7.md#上报监控数据)。
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


