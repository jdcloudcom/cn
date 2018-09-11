# 快速入门

请确认您已经熟悉OSS的基本概念，如Bucket、Object、Endpoint、AccessKeyId和AccessKeySecret等。

本节您将看到如何快速使用Java SDK，完成进行常见操作，如创建存储空间、上传文件、下载文件等。

##初始化JingdongStorageService

向云存储发送任一HTTP请求之前，必须先创建一个JingdongStorageService实例:
```
//访问京东云的accessKey  
String accessKey = "<yourAccessKeyId>";  
String secreteKey = "<yoursecretKeyId>";    
//endpoint以华北-北京为例  
String endpoint = "oss.cn-north-1.jcloudcs.com";  
 
//创建JingdongStorageService实例  
JingdongStorageService jss= new JingdongStorageService(accessKey,secreteKey);  
jss.setEndpoint(endpoint);  
 
//使用对象存储  
  
//销毁JingdongStorageService实例  
jss.destroy();
```
提示：更多OSSClient初始化的内容请参考“初始化”。

## 创建Bucket

存储空间(Bucket)是OSS全局命名空间，相当于数据的容器，可以存储若干文件(Object)。以下代码展示如何新建一个Bucket：
```
// 创建bucket  
String bucketName = "<your-bucket-name>";  
jss.createBucket(bucketName);
```
提示：

Bucket的命名规范，参见“基本概念”中的命名规范。

更多创建Bucket的信息，请参见“管理Bucket”。

## 上传Object

以下代码展示如何上传文件(object)至OSS：
```
File file = new File("D:/test");
String bucketName =  "<your-bucket-name>";
String objectName =  "<your-object-name>";
ObjectService objectService = jss.bucket(bucketName).object(objectName);
//获取输入流  
InputStream inputStream = new FileInputStream(file);  
//获取流长度  
long contentLength = file.length();  
//设置上传文件Content-type为"text/html"。函数返回上传数据的Etag  
String md5 = objectService.entity(contentLength,inputStream).contentType("text/html").put();
```
提示：

Java SDK通过InputStream上传Object至OSS。

更多上传Object的信息，请参见“上传文件”。

## 下载Object

以下代码展示如何获取Object的文本内容：
```
String bucketName =  "<your-bucket-name>";
String objectName =  "<your-object-name>";

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
```
提示：更多下载Object的信息，请参见“下载文件”。

## 列举Object

当完成一系列上传Object操作后，可能需要查看Bucket下包含哪些Object。以下代码展示如何列举指定Bucket下的Object：
```
//创建BucketService实例  
BucketService bucketService = jss.bucket(bucketName);  
//列出bucket下满足条件的文件和文件夹  
ObjectListing objectList = bucketService.listObject();  
//列出指定条件下的object名称  
for (ObjectSummary objectSummary : objectList.getObjectSummaries()) {  
     System.out.println("objectName : "+objectSummary.getKey());  
 }
```

## 删除Object

以下代码展示如何删除指定Object：
```
String bucketName =  "<your-bucket-name>";
String objectName =  "<your-object-name>";
 
//创建objectService实例    
ObjectService objectService = jss.bucket(bucketName).object(objectName);    
//删除object    
ObjectService.delete();
```
