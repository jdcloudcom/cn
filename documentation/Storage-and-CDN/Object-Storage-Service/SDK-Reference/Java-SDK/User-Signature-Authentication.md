# 使用URL签名授权访问

对象存储提供了一种基于查询字串(Query String)的认证方式，即通过预签名(Presigned)，为Object生成一个带有认证信息的URL，并将它分发给第三方用户来实现公开访问。在生成URL时，您可以指定URL过期的时间，从而限制用户长时间访问。

生成的URL默认以GET方式访问，这样，用户可以直接通过浏览器访问相关内容，代码如下：
```
// endpoint以华北-北京为例，其它region请按实际情况填写  
String endpoint = "oss.cn-north-1.jcloudcs.com";  
//您的AccessKey和SecretKey可以登录到对象存储的控制台，在【Access Key 管理】中查看。  
String accessKey = "<your accessKey>";  
String secretKey = "<your secretKey>";  
String bucketName = "<your bucketName>";  
String key = “<you objectKey>”;  
       
// 创建JingdongStorageService实例  
Credential credential = new Credential(accessKey, secreteKey);  
//默认配置文件。如用户需要个别配置，则自行配置。例:config.setMaxConnections(20);  
ClientConfig config = new ClientConfig();  
JingdongStorageService jss= new JingdongStorageService (credential, config);  
//设置Endpoint  
jss.setEndpoint(endpoint);  
      
//生成URL，可以通过浏览器直接访问，过期时间是1小时  
URI signatureUrl = jss.bucket(bucketName).object(key)
                   .generatePresignedUrl(3600);  
// 打印URL  
System.out.println(signatureUrl.toString());  
// 关闭jss  
jss.destroy();
```
