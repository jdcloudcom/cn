# 创建Bucket

您可以使用JingdongStorageService.createBucket创建Bucket。如下代码展示如何新建一个Bucket：

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
       
// 创建bucket  
String bucketName = "<your-bucket-name>";  
jss.createBucket(bucketName);  
//关闭jss  
jss.destroy();
```

提示：

* Bucket的命名规范，参见“基本概念”中的命名规范。

* Bucket的名字是全局唯一的，所以您需要保证Bucket名称不和别人的重复。

* 上面代码创建的bucket，权限是私有读写（默认权限）。
