# 删除文件

删除一个已存在的Object：
```
//您的AccessKey和SecretKey可以登录到京东云存储的控制台，在【Access Key 管理】中查看。    
String accessKey =  "<yourAccessKeyId>";    
String secreteKey = "<yourSecretKey>";         
// endpoint以华北为例，其它region请按实际情况填写    
String endPoint = "oss.cn-north-1.jcloudcs.com";    
String bucketName = "<yourBucketName>";    
String objectName = "<yourObjectName>";        
//ClientConfig当前为默认配置，用户可根据需要自行配置，如设置连接超时时间等    
ClientConfig config = new ClientConfig();       
     
//构造JingdongStorageService实例    
Credential credential = new Credential(accessKey, secreteKey);    
JingdongStorageService jss = new JingdongStorageService(credential,config); 
//配置endPoint    
jss.setEndpoint(endPoint);    
            
//创建objectService实例    
ObjectService objectService = jss.bucket(bucketName).object(objectName);    
//删除object    
objectService.delete();            
    
//JingdongStorageService对象内部维护一组HTTP连接池，在不使用该对象之前需要调用其destroy方法关闭连接池，    
//请注意，一旦调用destroy方法，该对象就不能再次被使用，否则将会抛出异常。    
jss.destroy();
```
