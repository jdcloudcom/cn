# 移动文件

在同一个区域中，可以将Object从一个Bucket移动到另外一个Bucket。相同的bucket下移动相当于重命名object。该操作不会修改metadata：
```
//您的AccessKey和SecretKey可以登录到京东对象存储的控制台，在【Access Key 管理】中查看。  
String accessKey =  "<yourAccessKeyId>";  
String secreteKey = "<yourSecretKey>";       
// endpoint以华北-北京为例，其它region请按实际情况填写  
String endPoint = "oss.cn-north-1.jcloudcs.com";  
String sourceBucketName = "< yourSourceBucketName >";//moveObject的源bucket  
String sourceKey = "<yourSourceKey>";//moveObject的源object key     
String destinationBucketName = "<yourDestinationBucketName>";//moveObject的目的bucket  
String destinationKey = "yourDestinationKey";//moveObject的目的object key  
//ClientConfig当前为默认配置，用户可根据需要自行配置，如设置连接超时时间等  
ClientConfig config = new ClientConfig();  
  
//构造JingdongStorageService实例  
Credential credential = new Credential(accessKey, secreteKey);  
JingdongStorageService jss = new JingdongStorageService(credential,config);  
//配置endPoint  
jss.setEndpoint(endPoint);    
  
//创建objectService实例  
ObjectService MoveObjectService = jss.bucket(destinationBucketName).object(destinationKey);  
//将sourceBucket下的sourceObject移动到destinationBucket下的destinationObject,返回移动后object的etag和lastModified  
MoveObjectResult moveObjectResult = MoveObjectService.moveFrom(sourceBucketName, sourceKey).move();  
System.out.println("LastModified : "+moveObjectResult.getLastModified());  
System.out.println("Etag : "+moveObjectResult.getEtag());  
    
//JingdongStorageService对象内部维护一组HTTP连接池，在不使用该对象之前需要调用其destroy方法关闭连接池，  
//请注意，一旦调用destroy方法，该对象就不能再次被使用，否则将会抛出异常。  
jss.destroy();
```
