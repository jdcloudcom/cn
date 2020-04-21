### **私有网络中创建云主机实例** 


## **概述**

通过此教学您可以完成在京东智联云上简单的网络部署，并获得以下资源：

- 1个私有网络
- 1个子网
- 1台云主机



### **操作步骤**

#### **第一步：创建私有网络**

- 在左边栏餐单中依次点击网络->私有网络->私有网络，进入私有网络列表页，点击创建，弹出创建配置窗口。
- 根据需求选择的地域，填写名称，填写CIDR，点击创建即可获得1个私有网络。

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Create-Virtual-Machine-Instance-In-VPC/Step1.png)



#### **第二步：创建子网**

- 在左边栏餐单中依次点击网络->私有网络->子网，进入子网列表页，点击创建，弹出创建配置窗口。
- 根据需求选择的地域，选择刚刚创建的私有网络，填写子网名称，填写子网CIDR，选择关联路由表，点击创建即可获得1个子网。

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Create-Virtual-Machine-Instance-In-VPC/Step2.png)



#### **第三步：在该子网中创建云主机**

- 在左边栏餐单中依次点击弹性计算->云主机->实例，进入实例列表页，点击创建，弹出创建配置窗口。
- 在实例创建的配置页找到网络模块，选择刚刚创建的私有网络和子网，其余配置根据云主机向导即可，点击创建即可创建1台指定私有网络、子网的云主机。

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Create-Virtual-Machine-Instance-In-VPC/Step3.png)