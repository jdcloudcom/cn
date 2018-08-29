- ### 一、    适用范围

  主机安全产品仅适用于京东云云主机，其他云厂商主机系统及物理机不适用该产品。请确认主机安全包在京东云主机上运行安装。

  ### 二、    官方下载地址

  1.《主机安全安装手册》下载地址：<https://hids.oss.cn-east-1.jcloudcs.com/hips_manual.docx>

  2.外网下载地址：

  Windows客户端：

  外网访问域名：<https://hids.oss.cn-east-1.jcloudcs.com/jcloudhids_v1.0_Installer.exe>

  64位Linux客户端：

  外网访问域名：<https://hids.oss.cn-east-1.jcloudcs.com/jcloudhids_linux64_V1.0.tar.gz>

  \3. 内网下载地址：

  Windows客户端：

  内网访问域名：<https://hips.jdcloud.com/jcloudhids_v1.0_Installer.exe>

  64位Linux客户端：

  内网访问域名： <https://hips.jdcloud.com/jcloudhids_linux64_v1.0.tar.gz>

  ### 三、Windows系统安装说明

  1、软件获取：

  请确认主机安全软件包已下载到云主机，如图1：

  ![img](https://img1.jcloudcs.com/cms/52a493d5-3005-41e0-92ae-a7ad111529ad20170626123325.png)

  图1

  2 、 双击下载下来的软件。如图2

  ![img](https://img1.jcloudcs.com/cms/c9183ecf-3b5b-4f5e-a73c-409335a2c4f820170626123537.png)

  图2

  3、点击“运行”按钮。按照提示，点击“下一步”按钮，如图3：

  ![img](https://img1.jcloudcs.com/cms/a3de1bf9-06a9-49c9-b2a1-5e2c5001fd9620170626123726.png)

  图3

  4、   点击“我接受”按钮，如图4：

  ![img](https://img1.jcloudcs.com/cms/88deb22d-1655-4ffd-b773-5f3b479dcd3020170626123833.png)

  图4

  5、 可以选择安装路径，再点击“下一步”按钮，如图5：

  ![img](https://img1.jcloudcs.com/cms/b701a89a-e0fb-4972-bed5-74b4b11b18d020170626123916.png)

  图5

  6、    选择“开始菜单”文件夹，并点击“安装”按钮，如图6：

  ![img](https://img1.jcloudcs.com/cms/f7cbee27-3029-4c6c-9bc3-999c22f6b70620170626124000.png)

  图6

  7、    程序开始安装，如图7：

  ![img](https://img1.jcloudcs.com/cms/d969ef9b-53b1-479f-8293-9f5574366e8e20170626124146.png)

  图7

  8、 安装完成，点击“完成”按钮，安装完成。

  ![img](https://img1.jcloudcs.com/cms/53b47fd3-71da-4a02-ac81-800c4200d95c20170626124223.png)

  图8

  9、完成安装。

  ### 四、Linux系统安装说明 

  \1. 软件获取路径：利用wget命令，获取软件。
      $ wget https://hids.oss.cn-east-1.jcloudcs.com/jcloudhids_linux64_V1.0.tar.gz

  \2. 将下载的文件解压。
      $ tar xvf jcloudhids_linux64_v1.0.tar.gz
  \3. 进入解压的文件路径：
      $ cd jcloudhids_linux64_v1.0/
  \4. 安装程序，用户需要有sudo权限：
      $ sudo ./install.py
  \5. 安装完成，如图9：
      $ sudo ./install.py

  ![img](https://img1.jcloudcs.com/cms/8c4ba2d2-4f35-40b4-aa31-29d698e2c21820170626124803.png)

  图9
