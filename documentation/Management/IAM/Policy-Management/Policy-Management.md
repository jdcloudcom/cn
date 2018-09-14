主账号是资源的所有者，是为资源实际付费的人，拥有资源的完全控制权；子账号不拥有任何资源，默认没有任何资源访问权限；只有得到主账号的授权时，子账号才能通过控制台或 API 访问特定的资源。

主账号授权子账号的方式，是为子账号（或其所在的群组）附加授权策略。子账号所拥有的资源访问权限，是子账号和其所在的群组附加的授权策略的合集。

授权策略（Policy）是描述一条或多条权限的 JSON 文档。主账号通过创建策略、将策略附加到子账号或群组，来完成对子账号或群组的授权。

本文介绍了如何在控制台查看策略内容和授权情况、创建策略、将策略附加到子账号和群组，及从子账号和群组的权限中移除策略。

# 查看策略
登录控制台，进入 访问控制 > 授权策略管理，可以查看所有的系统策略和自定义策略。
策略的 引用次数 是该条策略已经被附加的实体数目，包括子账号和群组。对于系统策略，不支持您进行修改或删除；但您可以创建、修改或删除您的自定义策略。
![查看策略1](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Strategy%20Management/%E6%9F%A5%E7%9C%8B%E7%AD%96%E7%95%A51.jpg)
点击 策略名，进入策略详情页面。在 基本信息 中，有两种方式查看策略信息。
第一种是可视化策略，列举了该策略文档中授权的所有资源和操作。
第二种是 JSON 格式文档。
在 授权策略记录 中，可以查看子账号或群组添加、解除授权策略的记录。
![查看策略2](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Strategy%20Management/%E6%9F%A5%E7%9C%8B%E7%AD%96%E7%95%A52.jpg)
![查看策略3](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Strategy%20Management/%E6%9F%A5%E7%9C%8B%E7%AD%96%E7%95%A53.jpg)
![查看策略4](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Strategy%20Management/%E6%9F%A5%E7%9C%8B%E7%AD%96%E7%95%A54.jpg)

# 创建策略
在 授权策略管理 列表页面，点击【创建】按钮，支持两种创建自定义策略的方式。第一种是便利化策略生成器，第二种是 JSON 策略编辑器。
![创建策略](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Strategy%20Management/%E5%88%9B%E5%BB%BA%E7%AD%96%E7%95%A5.jpg)

# 便利化策略生成器
在便利化策略生成器中，支持通过可视化的方式选择资源类型、资源 IDs、操作权限，生成一组或多组权限。
![便利化策略生成器](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Strategy%20Management/%E4%BE%BF%E5%88%A9%E5%8C%96%E7%AD%96%E7%95%A5%E7%94%9F%E6%88%90%E5%99%A8.jpg)

例如，选择对云主机进行授权，然后点击 添加资源，在如下图所示的窗口中选择需要授权的云主机实例：

 - 授权主账号下所有（包括所有区域）的云主机资源，包括未来新购的资源，则勾选 a 选择框并确定；
 - 授权当前区域已购的云主机资源，则勾选 b，点击选择箭头并确定；
 - 授权当前区域部分资源，则根据需求勾选 c，点击选择箭头并确定。

注：切换了地域后，需要重新选择资源。
![重新选择资源](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Strategy%20Management/%E9%87%8D%E6%96%B0%E9%80%89%E6%8B%A9%E8%B5%84%E6%BA%90.png)

完成一组资源权限配置后，可以 继续添加权限，直到完成策略设置。
![继续添加权限](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Strategy%20Management/%E7%BB%A7%E7%BB%AD%E6%B7%BB%E5%8A%A0%E6%9D%83%E9%99%90.jpg)

点击【下一步】按钮，填写策略名称和描述后，即可 生成策略。
![生成策略](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Strategy%20Management/%E7%94%9F%E6%88%90%E7%AD%96%E7%95%A5.jpg)

# JSON 策略生成器
在 JSON 策略生成器中，您可以直接编写 JSON 策略，也可以先选择一个策略模板，再进行 JSON 文档编辑。
![Json 选择模板](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Strategy%20Management/Json%20%E9%80%89%E6%8B%A9%E6%A8%A1%E6%9D%BF.jpg)

点击【选择模板】按钮，可以选择一条系统策略或自定义策略作为模板。
![Json 选择模板2](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Strategy%20Management/Json%20%E9%80%89%E6%8B%A9%E6%A8%A1%E6%9D%BF2.jpg)

如果需要在已选择的策略模板上，再添加其他权限，可以点击 添加权限，通过便利化的方式来完成。
![添加其他权限](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Strategy%20Management/Json%20%E6%B7%BB%E5%8A%A0%E6%9D%83%E9%99%90.png)
最后，根据授权需求，对生成的 JSON 策略进行编辑，完善策略名称和描述后，即可生成一条自定义策略。

# 添加或解除子账号（群组）的授权策略
在 用户管理 页面，可以为子账号添加授权。
![为子账号添加授权](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Strategy%20Management/%E4%B8%BA%E5%AD%90%E8%B4%A6%E5%8F%B7%E6%B7%BB%E5%8A%A0%E6%8E%88%E6%9D%83.jpg)
![为子账号添加授权](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Strategy%20Management/%E4%B8%BA%E5%AD%90%E8%B4%A6%E5%8F%B7%E6%B7%BB%E5%8A%A0%E6%8E%88%E6%9D%832.png)

在 用户详情 > 用户授权策略 页面，可以 添加 或 解除 子账号的授权。
![添加或解除子账号的授权](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Strategy%20Management/%E5%8A%A0%20%E6%88%96%20%E8%A7%A3%E9%99%A4%20%E5%AD%90%E8%B4%A6%E5%8F%B7%E7%9A%84%E6%8E%88%E6%9D%83.jpg)

在 群组管理 页面，可以为群组添加授权。
![为群组添加授权](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Strategy%20Management/%E4%B8%BA%E7%BE%A4%E7%BB%84%E6%B7%BB%E5%8A%A0%E6%8E%88%E6%9D%83.jpg)

在 群组详情 > 群组授权策略管理 页面，可以 添加 或 解除 群组的授权。
![添加或解除群组的授权](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/Strategy%20Management/%E6%B7%BB%E5%8A%A0%20%E6%88%96%20%E8%A7%A3%E9%99%A4%20%E7%BE%A4%E7%BB%84%E7%9A%84%E6%8E%88%E6%9D%83.jpg)

