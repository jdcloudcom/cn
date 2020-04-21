## **标准WEB+APP+DB架构服务部署**

### **概述**

通过此教学您可以在京东智联云完成基础的网络模型部署，一个负责对外的WEB层一个负责逻辑的APP层一个负责数据的数据库层，并获得以下资源：

- 1个私有网络
- 3个子网



### **操作步骤**

#### **第一步：创建私有网络**

- 在左边栏餐单中依次点击网络->私有网络->私有网络，进入私有网络列表页，点击创建，弹出创建配置窗口。
- 根据需求选择的地域，填写名称，填写CIDR，点击创建即可获得1个私有网络。

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Standard-WEB-APP-DB-Architectural-Service-Deployment/Step1.png)



#### **第二步：创建子网WEB层、APP层、DB层子网**

- 在左边栏餐单中依次点击网络->私有网络->子网，进入子网列表页，点击创建，弹出创建配置窗口。
- 根据需求选择的地域，选择刚刚创建的私有网络，填写子网名称，填写子网CIDR，选择关联路由表，点击创建即可。重复三遍即可获得3个子网。

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Standard-WEB-APP-DB-Architectural-Service-Deployment/Step2-1.png)

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Standard-WEB-APP-DB-Architectural-Service-Deployment/Step2-2.png)

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/Standard-WEB-APP-DB-Architectural-Service-Deployment/Step2-3.png)