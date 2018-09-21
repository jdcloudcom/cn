# 删除Bucket

您可以使用JingdongStorageService.deleteBucket删除Bucket。以下代码展示如何删除一个Bucket：
```
// endpoint以华北-北京为例，其它region请按实际情况填写  
String endpoint = "oss.cn-north-1.jcloudcs.com";  
//您的AccessKey和SecretKey可以登录到对象存储的控制台，在【Access Key 管理】中查看。  
String accessKey = "<yourAccessKey>";  
String SecretKey = "<yourSecretKey>";  
      
// 创建JingdongStorageService实例  
Credential credential = new Credential(accessKey, secreteKey);  
//默认配置文件。如用户需要个别配置，则自行配置。例:config.setMaxConnections(20);  
ClientConfig config = new ClientConfig();  
JingdongStorageService jss= new JingdongStorageService (credential, config);  
//设置Endpoint  
jss.setEndpoint(endpoint);  
      
// 删除bucket  
jss.deleteBucket("<bucketName>");  
// 关闭jss  
jss.destroy();
```
提示：

* 如果Bucket不为空(即Bucket中有文件或者分片上传碎片），则Bucket无法删除；

* 必须先删除Bucket中的所有文件后，Bucket才能成功删除。

* 必须先删除Bucket中的访问控制权限后，Bucket才能成功删除
