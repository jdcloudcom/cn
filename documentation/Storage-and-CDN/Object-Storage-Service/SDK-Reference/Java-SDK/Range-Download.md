# 范围下载

如果OSS文件较大，并且只需要其中一部分数据，可以使用范围下载，下载指定范围的数据。如果指定的下载范围是0-1000，则返回第0到第1000个字节的数据，包括第1000个，共1001字节的数据，即[0, 1000]。如果指定的下载范围是1000-，则返回数据跳过前1000个字节，将其余部分下载：
```
//您的AccessKey和SecretKey可以登录到对象存储的控制台，在【Access Key 管理】中查看。  
String accessKey =  "<yourAccessKeyId>";  
String secreteKey = "<yourSecretKey>";       
//endpoint以华北为例，其它region请按实际情况填写  
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
//获取object，其中数据返回第0到第1000个字节的数据，包括第1000个，共1001字节的数据  
StorageObject storageObject = objectService.range(0, 1000).get();  
//获取object,其中返回数据跳过前1000个字节，其余部分下载到本地文件” localFile”中  
//StorageObject storageObject = objectService.range(1000).get();  
//将文件下载到本地文件中，如下示例是将指定的object下载到"localFile"中  
storageObject.toFile(new File("<localFile>"));    
 
//JingdongStorageService对象内部维护一组HTTP连接池，在不使用该对象之前需要调用其destroy方法关闭连接池，  
//请注意，一旦调用destroy方法，该对象就不能再次被使用，否则将会抛出异常。  
jss.destroy();
```
提示：假如需要从OSS流式读取64KB的数据，请使用如下的方式多次读取，直到读取64KB或者文件结束：
```
byte[] buf = new byte[1024];  
InputStream in = storageObject.getInputStream();  
for (int n = 0; n != -1; ) {  
    n = in.read(buf, 0, buf.length);  
}  
in.close();
```
而不是如下的形式：
```
byte[] buf = new byte[64 * 1024];  
InputStream in = storageObject.getInputStream();  
in.read(buf, 0, buf.length);  
in.close();
```
原因是，流式读取一次不一定能读到全部数据，详细说明请参考InputStream.read。
