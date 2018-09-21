# 安装

## 环境准备

适用于JDK 6及以上版本。

## 安装方式

**在Eclipse项目中导入JAR包：**

以1.0.3版本为例，步骤如下：

1. 下载Java SDK开发包[Java SDK](http://downloads.oss.cn-north-1.jcloudcs.com/jfs-jcloud-sdk-java-1.0.3-SNAPSHOT.jar)

2. 解压该开发包。

3. 将解压后文件夹中的文件： jfs-jcloud-sdk-java-<versionId>.jar 以及demo工程lib文件夹下的所有文件拷贝到您的项目中。

4. 在Eclipse中选择您的工程，右击选择Properties > Java Build Path > Add JARs。

5. 选中您在第3步拷贝的所有JAR文件。

经过以上几步，您就可以在Eclipse项目中使用OSS Java SDK。


## 示例工程

OSS Java SDK提供示例工程，您可以在本地设备上运行示例工程。您也可以以示例工程为基础开发您的应用。

* 示例工程：[jfs-jdcloud-sdk-java-demo.zip](http://downloads.oss.cn-north-1.jcloudcs.com/jfs-jcloud-sdk-java-demo.zip)

* 示例工程中，提供丰富的示例程序，方便用户参考或直接使用

示例包括以下内容：

|示例文件|示例内容|
|-|-|
|JcloudOSSDemo|展示了使用云存储的快速入门示例|
|InitOSSSample|展示了OSS初始化的方法|
|ObjectSample|展示了基本的object相关操作，如上传，下载，删除等|
|PutObjectSample|展示了简单文件上传的用法|
|GetObjectsample|展示了文件下载的用法|
|DeleteObjectSample|展示了删除文件的用法|
|MoveObjectSample|展示了移动文件的用法|
|ListObjectSample|展示了列举文件的用法|
|PresignedUrlSample|展示了创建带预签名URI的用法|
|BucketSample|展示了存储空间配置的用法，包括存储空间的基本操作（创建、删除、显示该账户所有的存储空间）、防盗链相关操作等|
|MultipartUploadSample|展示了大文件的分片上传的用法|
