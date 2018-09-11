# 简单下载

OSS Java SDK提供了丰富的文件下载接口，用户可以通过以下方式从OSS中下载文件：

* 流式下载

* 下载到本地文件

* 范围下载(Range下载)

流式下载、下载到本地文件称为简单下载。

## 流式下载

在进行大文件下载时，往往不希望一次性处理全部内容，而是希望流式地处理，一次处理一部分内容。
```
//您的AccessKey和SecretKey可以登录到对象存储的控制台，在【Access Key 管理】中查看。  
String accessKey =  "<yourAccessKeyId>";  
String secreteKey = "<yourSecretKey>";       
// endpoint以华北-北京为例，其它region请按实际情况填写  
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
 
//获取object对象  
StorageObject storageObject = objectService.get();  
// 读Object内容  
System.out.println("Object content:");  
BufferedReader reader = new BufferedReader(new InputStreamReader(storageObject.getInputStream()));  
String tempString = null;  
// 一次读入一行，直到读入null为文件结束  
while ((tempString = reader.readLine()) != null) {  
    System.out.println(tempString);  
}  

reader.close();       
storageObject.close();  
 /JingdongStorageService对象内部维护一组HTTP连接池，在不使用该对象之前需要调用其destroy方法关闭连接池，  
//请注意，一旦调用destroy方法，该对象就不能再次被使用，否则将会抛出异常。  
jss.destroy();
```
提示：

* 获取的流一定要显示close，否则会造成资源泄露

* 假如需要从OSS流式读取64KB的数据，请使用如下的方式多次读取，直到读取64KB或者文件结束：
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

## 下载到本地文件

把Object的内容下载到指定的本地文件中。如果指定的本地文件不存在则会新建。
```
//您的AccessKey和SecretKey可以登录到京东云存储的控制台，在【Access Key 管理】中查看。  
String accessKey =  "<yourAccessKeyId>";  
String secreteKey = "<yourSecretKey>";       
// endpoint以华北-北京为例，其它region请按实际情况填写  
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

//获取object对象  
StorageObject storageObject = objectService.get();  
//将文件下载到本地文件中，如下示例是将指定的object下载到"localFile"中  
storageObject.toFile(new File("<localFile>"));  

 
//JingdongStorageService对象内部维护一组HTTP连接池，在不使用该对象之前需要调用其destroy方法关闭连接池，  
//请注意，一旦调用destroy方法，该对象就不能再次被使用，否则将会抛出异常。  
jss.destroy();
```
